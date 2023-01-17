# italiaKIT API

Questo repository contiene la descrizione, con specifica **OpenAPI**, di tutti gli endpoint del servizio [italiaKIT](https://www.italiakit.it).

OpenAPI è una specifica per la descrizione di interfacce di programmazione delle applicazioni (API) in modo che possano essere utilizzate da altre applicazioni.
La specifica è basata su un formato di file JSON o YAML, in cui vengono descritte le operazioni supportate dall'API, i parametri di input e di output, l'autenticazione e altre informazioni.


## Che cos'e italiaKIT API ?

ItaliaKIT API e' un servizio Rest API che mette a disposizione le informazioni riguardanti le **Regioni**, **Province** e **Comuni** italiani.

Rimandiamo alla documentazione per ulteriori informazione sul [servizio](https://www.italiakit.it/intro).

## Endpoint

Attualemente la ```v1```  ha 4 endpoint 

### GetAll : 

Restituisce tutte le informazioni delle regioni, province e comuni in unico **JSON**. 

| HTTP Metodo | Endpoint URL                                                | Nome Richiesta |
|-------------|-------------------------------------------------------------|----------------|
| GET         | /api/v1/italia  | GetAll         |


### GetRegioneByName : 

Restituisce tutte le informazioni della regione indicata compreso le province e i comuni.


| HTTP Metodo | Endpoint URL                                     | Nome Richiesta |
|-------------|--------------------------------------------------|----------------|
| GET         | /api/v1/italia/regioni/{nome_regione} </SpanURL> | GetRegione     |


### GetProvinciaByName

Restituisce tutte le informazioni della provincia indicata e tutti i comuni che la compongono.


| HTTP Metodo                                | Endpoint URL                              | Nome Richiesta     |
|--------------------------------------------|-------------------------------------------|--------------------|
| <StyleCRUD color="#25c2a0">GET</StyleCRUD> | /api/v1/italia/provincia/{nome_provincia} | GetProvinciaByName |


### GetComuneByName

Restituisce informazioni del comune indicato. 

| HTTP Metodo                                | Endpoint URL                                                                     | Nome Richiesta           |
|--------------------------------------------|----------------------------------------------------------------------------------|--------------------------|
| <StyleCRUD color="#25c2a0">GET</StyleCRUD> | /api/v1/italia/comune/{nome_comune}  | GetComuneByProvinciaName |


## Modello 

![Schema](https://github.com/y00ss/italia-kit-openAPI/blob/c935279cc4b930138ae49e2f8ba15eeaa2e436a8/img/schema.svg?raw=true)


### Regione
I campi della Regione sono da ``` 3-6```



| Nome campo    | Descrizione                          | Tipo   |
|---------------|--------------------------------------|--------|
| name          | Nome della Regione                   | String |
| wiki          | Link (url) Wipedia della Region      | String |
| cod_reg_istat | Codice Istat Regione                 | Int    |
| repartition   | Rappresenta la posizione geografica  | Int    |



### Provincia
I campi della Provincia sono da ``` 7-16```. Province e; una ```Lista``` contenente tutte le province che appartengono alla Regione

| Nome campo | Descrizione                          | Tipo   |
|------------|--------------------------------------|--------|
| id         | Sigla della provincia                | String |
| name       | Nome provincia                       | String |
| info       | Informazioni provincia               | Object |
| population | Popolazione totale provincia         | Int    |
| area_kmq   | Area totale in km quadrati provincia | Doble  |
| density    | Densita' popolazione x km^2          | Doble  |
| wiki       | Link (url) pagin wikipedia Provincia | String |




### Comune

I campi del Comune sono da  ```17, 32```.  Il campo ```comune``` e' una ```Lista``` contenente tutti i Comuni appartenti alla Provincia.

| Nome campo    | Descrizione                            | Tipo   |
|---------------|----------------------------------------|--------|
| id            | Codice identificativo Comune           | String |
| name          | Nome Comune                            | String |
| cod           | Oggetto contente codici amministrativi | Object |
| cod_ente      | Codice elettorale                      | String |
| cod_istat     | Codice Istat                           | String |
| cod_catastale | Codice catastale                       | String |
| contact       | Oggetto contenente contatti del Comune | Object |
| email         | Contatto email Comune                  | String |
| pec           | Contatto email certificata             | String |
| tel           | Contatto telefonico                    | String |
| fax           | Contatto Fax                           | String |
| cap           |  Codice di Avviamento Postale          | Int    |


## Fonti

Le fonti dei dati provengono :

- [Dipartimento per gli Affari Interni e Territoriali](https://dait.interno.gov.it/)
- [Istituto Nazionale di Statistica](https://demo.istat.it/)
- [Poste Italiane](https://www.poste.it/index.html)

## Feutures ? 

Implementazione di **GraphQL**
