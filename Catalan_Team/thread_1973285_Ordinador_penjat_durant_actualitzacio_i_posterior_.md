---
title: "Ordinador penjat durant actualitzacio i posterior drama: impossible arrencar-lo"
date: 2012-05-04
forum: Catalan Team
---

### Post by lo gambusí on 2012-05-04
Hola,

Un classic, no? Estava actualitzant a la darrera versio d'Ubuntu, necessitava consultar un pdf i entre navegador web i pdfs he petat la instal.lacio.

Ara en engegar l'ordinador no se'm carrega l'entorn grafic. Em surt la pantalla negra rotllo consola / linia d'ordres (no conec lo terme concret, disculpeu-me) amb el seguent missatge:

> Ubuntu 12.04 LTS oriol-laptop tty
oriol-laptop login:

Que hauria de fer per recuperar la instal.lacio o com a minim accedir al material que tenia ans d'emmerdar la cosa? No m'importa reinstal.lar lo SO des de zero, pero si no puc recuperar la informacio sera una putada grossa grossa. Com es tambe classic, hi ha bastant material del qual no tinc copia de seguretat.

Si em poguesseu ajudar em farieu un favor enorme. He d'entregar un treball dimarts vinent i estic força cagat ara mateix.

Disculpeu la manca d'accents i puntuacio, estic en un teclat frances.

Moltes gracies per l'atencio

---

### Post by wgarcia on 2012-05-04
El primer que faria és aconseguir un USB o CD autònom (és a dir arrencable amb Ubuntu), l'engegaria, muntaria el disc on tens les dades, buscaria "/home/el_teu_usuari" i intentaria copiar les dades més importants per si tot va malament per no perdre les teves dades. En general és recomanable sempre anar fent còpies de seguretat, no sols en cas d'actualització, sinó en general, perquè estem parlant de màquines que sempre poden fallar. I haven-t'hi l'Ubuntu One amb 5 gigues gratis i les eines de còpia de seguretat de l'Ubuntu la veritat és que no hi ha excusa.

Ara, respecte al teu problema, si accedeixes a la línia de comandes tens molt guanyat. Entra el teu usuari i clau, i després entra per començar les ordres:

```
sudo apt-get update
sudo apt-get upgrade
```

a veure si continua l'actualització.

---

### Post by lo gambusí on 2012-05-04
Gracies per la resposta, company.

Per CD autonom vols dir descarregar un ISO i enregistrar l'instal.lador de l'Ubuntu per a despres iniciar sessio co, a LIVE CD? Si es aixi, un cop fet aixo tinc el disc muntat i hi puc accedir? O he de fer quelcom? Merci

---

### Post by lo gambusí on 2012-05-04
Perfecte, fet i arreglat. Molt agrait; de tot cor!:KS

---

