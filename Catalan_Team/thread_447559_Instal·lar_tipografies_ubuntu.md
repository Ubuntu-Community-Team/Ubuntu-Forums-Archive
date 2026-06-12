---
title: "Instal·lar tipografies ubuntu"
date: 2007-05-18
forum: Catalan Team
---

### Post by bratac on 2007-05-18
Bones, 

vull instal·lar una tipografia a ubuntu i en una web m'han dit que faci :

Alt + F2 

després he escrit: gksu nautilus fonts:///

i he copiat la tipografia a la carpeta de tipografies que em diu.

El problema és que després he reiniciat l'ordinador i no puc agafar aquesta tipografia. 

He fet alguna cosa malament? 

Ho puc fer d'alguna altra manera? 

Necessito la tipografia urgentment. La tipografia és ttf i abans la tenia instal·lada a ubuntu.

fins ara, 

Alfred

---

### Post by patrickfromspain on 2007-05-18
ves a /usr/share/fonts/truetype, i alla o hi crees una carpeta nova i hi poses la font o la poses directament a alguna de les carpetes.

salut!

---

### Post by CarlesOriol on 2007-05-18
Has instal·lat la tipografia a l'usuari administrador.

Has de fer el mateix sense el gksu. No cal que reinicis res. N'hi ha prou en tancar el programa on la vols usar com a molt.

La so&#320;lució d'en Patrick funciona però no és la més correcta a nivell d'usuari.

---

### Post by lluisanunez on 2007-05-20
I per desinsta&#320;lar?
Tinc una llarga llista de fonts àrabs i índies que no necessito per a res. Si obro la meva carpeta fonts:/// les veig protegides (no les puc esborrar). Si vaig a fonts:/// com a superuser és una altra carpeta, oi? Si les **sudo** esborro de /usr/share/fonts és una manera correcta de desinsta&#320;lar.les?

---

### Post by CarlesOriol on 2007-05-20
Desinstala el paquet que les ha carregat.

pots localitzar-lo amb dpkg -S nomdelarxiufont

El cas concret que tu dius és el ttf-arabeyes

---

### Post by lluisanunez on 2007-05-20
Gràcies! És potent això del **dpkg**

---

