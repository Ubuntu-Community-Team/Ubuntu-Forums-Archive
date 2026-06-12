---
title: "[SOLVED] INPROCOMM Ipn2220 ERA: Wifi no funciona"
date: 2007-10-28
forum: Catalan Team
---

### Post by xtort on 2007-10-28
Tinc un portatil packard bell amb Ubuntu 7.10 i no aconsegueixo fer funcionar el wifi, el xip es el inprocom, l'hi vaig instal·lat el driver (neti2220.inf) amb el ndiswrapper ,  el problema es que el wifi del pc es desactiva quan es carrega el Ubuntu(la llum que indica el funcionament del wifi s'apaga)
Si entro a la configuració manual de la xarxa i desactivo i activo el clic que te devant de la xarxa sense fils “a vegades (1 de cada 20)” es posa a funcionar, però quan paro i torno a engegar tornem a estar sense wifi.
Que puc fer per tenir sempre funcionant el wifi? 
 Salut ubuntaires

---

### Post by papapep on 2007-10-28
I quin moden en concret són de portàtil i de tarja wifi?

---

### Post by xtort on 2007-10-28
No entenc la pregunta
Salut

---

### Post by papapep on 2007-10-28
Volia dir "model", no "moden". :-)

---

### Post by xtort on 2007-10-28
El portatil es un EASYNOTE A5340 i el wifi està integrat en el pc i és un mòdul INPROCOMM  Ipn2220.

---

### Post by Ferri on 2007-10-28
He trobat un altre fil que diu que aquesta tarja els funcionava bé a Feisty però no a Gutsy. Sembla que fent servir la kernel de Feisty a Gutsy sí que funciona, però només és un que ho diu i, per tant, no és massa segur que funcioni en general.
[InProComm IPN2220 i Gutsy]("http://ubuntuforums.org/showthread.php?t=586414&highlight=ipn2220")

---

### Post by xtort on 2007-10-28
Jo diria que no es un problema de incompatibilitat amb Gusty, perquè ara estic escribint des de wifi amb Gusty, si bé es cert que per aconseguir-ho e tingut que reiniciar unes quantes vegades.
Jo crec que el problema està en la carga d'Ubuntu, que li envia alguna instrucció al wifi que l'atura.

---

### Post by patrickfromspain on 2007-10-28
jo tinc un toshiba satellite L10 amb aquesta tarja inalambrica i va perfectament be.

salut

---

### Post by xtort on 2007-10-28
Acabo de solucionar-ho, buscant respostes per internet he trobat en una pagina francesa uns drivers mes nous que els que jo tenia, he reinstal·lat el ndiswrapper, li he posat els nous drivers i ha funcionar.
Salut

---

### Post by indifference on 2007-10-28
Podes me indicar la pagina?

Gracias.

---

### Post by xtort on 2007-10-28
No l'he guardat, jo nomes buscava el drivers.
Si els vols te'ls envio.
Salut

---

### Post by papapep on 2007-10-28
Seria interessant que posessis la url de la pàgina on els has trobat o, com a minim, el nom exacte de l'arxiu per poder-lo buscar més fàcilment.

---

### Post by xtort on 2007-10-29
El fitxer es diu “inprocomm_ipn2220_v3.07.02.2005.zip”
Salut

---

### Post by Ferri on 2007-10-30
Es pot trobar aquest arxiu en aquest mateix fòrum: [http://ubuntuforums.org/attachment.php?attachmentid=24433&d=1170478866](http://ubuntuforums.org/attachment.php?attachmentid=24433&d=1170478866)

---

