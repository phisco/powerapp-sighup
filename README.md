# POWERAPP WEB APPLICATION

Un esempio di un'applicazione con tre tier:
- frontend in PHP servito da Apache,
- backend in Nodejs 
- database Mongodb

## Frontend
Il nostro frontend usa l'immagine `sighup/kubeprimer-web` e ascolta sulla porta 80.
Vogliamo che il frontend abbia:
- 3 repliche
- 2 variabili d'ambiente settate:
  - `BACKEND_HOST` -> indirizzo del backend
  - `COMPANY` -> nome della compagnia per cui lavoriamo (ovviamente anche finta)
  - `SOME_PASSWORD`-> una password scelta da voi per accedere poi alla vostra app (Secret)

2) il nostro backend usa l'immagine `sighup/kubeprimer-backend` e ascolta sulla porta 80
Per backend basta avere solo una replica sola per adesso e ha bisogno di parlare con il database (mongodb)
- variabili d'ambiente settate:
  - MONGO_HOST -> l'indirizzo a cui raggiungere il databaseil database

3) Per il database usiamo `mongodb`. Attenzione che i database sono applicazioni Stateful. Quindi va creato il controller apposito. Per la persistenza dei dati abbiamo bisogno di un volume. 
Usiamo l'immagine `mongo:4.0-xenial` da dockerhub, andate sul dockerhub per vedere la specifica dell'immagine per capire che porta dovete esporre e dove vuole che gli sia montato il volume.

