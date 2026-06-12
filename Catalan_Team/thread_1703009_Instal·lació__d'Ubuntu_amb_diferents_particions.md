---
title: "Instal·lació  d'Ubuntu amb diferents particions"
date: 2011-03-08
forum: Catalan Team
---

### Post by Curial on 2011-03-08
Estic provant d'instal·lar l'ubuntu per netbook i quan arribo a la opció de reserva d'espai de disc em surt amb dues opcions (fer servir disc complet o especificació manual) i no tres (instal·lar juntament amb un altre SO).

Crec que és perquè ja de partida tinc quatre particions al disc (W7 boot,W7,HP recovery i HP tools lba), i no em deixa crear-ne més.

No sé si es possible instal·lar-lo en aquestes condicions o és completament necessari eliminar-ne una?

---

### Post by Funk'u on 2011-03-08
> Estic provant d'instal·lar l'ubuntu per netbook i quan arribo a la opció  de reserva d'espai de disc em surt amb dues opcions (fer servir disc  complet o especificació manual) i no tres (instal·lar juntament amb un  altre SO).Si tries especificació manual podràs triar com i on fer-ho, endavant les "atxes"!
> Crec que és perquè ja de partida tinc quatre particions al disc (W7  boot,W7,HP recovery i HP tools lba), i no em deixa crear-ne més.
Si vaig errat que em rectifiquin però encara en pots fer unes quantes més.
> No sé si es possible instal·lar-lo en aquestes condicions o és completament necessari eliminar-ne una?     Home necessari no..., però recomanable..., proba de borrar-les totes home, malaguanyat ordinador  :rolleyes:


Salut!

---

### Post by wgarcia on 2011-03-09
No es poden crear més de 4 particions al disc, per tant hauràs d'eliminar una i dedicar-la a Linux. Alguns ordinadors venen ara amb una partició d'utilitat del fabricant, una de recuperació de Windows, una de sistema de Windows i una altra de dades del Windows. 

El que es pot fer és doncs carregar-se aquesta última, la partició de dades del Windows, i convertir-la en una partició lògica. Dins de la partició lògica es poden crear tantes particions addicionals com vulguis. Òbviament si tens dades a aquesta partició primer s'han de fer còpies o passar-les a la partició de sistema del Windows. La partició de sistema de Windows convé que la defragmentis un parell de cops si la vols canviar de grandària.

---

### Post by Funk'u on 2011-03-09
> **wgarcia said:**
> No es poden crear més de 4 particions al disc... 
I això com és?

> **wgarcia said:**
> El que es pot fer és doncs carregar-se aquesta última, la partició de dades del Windows, i convertir-la en una partició lògica. Dins de la partició lògica es poden crear tantes particions addicionals com vulguis...A coi, no ho sabia, tenia els dos conceptes barrejats, perdoneu.   :oops:



Salut!

---

### Post by akyra on 2011-03-09
Crec que és important que miris quin espai tens a cada partició per poder decidir com redistribuir l'espai.

Funk'u, no pots tenir més de 4 particions primaries. Hauria de ser 3 primaries i una lògica. En aquesta lògica pots fer tantes particions com vulguis i és en aquestes a on pots instal·lar l'ubuntu sense problemes.
Si instal·las l'ubuntu, no és recomanble fer una unica partició, així que hauries de fer com a mínim les particions "/", "swap" i "/home", si en vols ver més es pot fer, depen de les teves necessitats.

Salutacions.

---

### Post by wgarcia on 2011-03-09
Que no es puguin crear més de 4 particions és una limitació històrica dels sistemes basats en processadors Intel, els discos del qual tenien inicialment una taula de particions que sols permetien 4. En poder fer una lògica i aquí posar tantes com es vulguin en realitat no hi ha limitació al nombre de particions, sols que no poden haver-hi més de 4 primàries.

---

### Post by akyra on 2011-03-09
Perdó volia dir 3 primaries i una extesa que pots emplenar de lògiques.

De fet si vols pots mirar aquí, [http://es.wikipedia.org/wiki/Partici%C3%B3n_de_disco]("http://es.wikipedia.org/wiki/Partici%C3%B3n_de_disco")

Adeu

---

### Post by Funk'u on 2011-03-09
> **akyra said:**
> 
Funk'u, no pots tenir més de 4 particions primaries. Hauria de ser 3 primaries i una lògica. En aquesta lògica pots fer tantes particions com vulguis i és en aquestes a on pots instal·lar l'ubuntu sense problemes.
Val sabia que podies fer-ne moltes, ara ho entenc un xic més tot plegat.
> **akyra said:**
> 
Si instal·las l'ubuntu, no és recomanble fer una unica partició, així que hauries de fer com a mínim les particions "/", "swap" i "/home", si en vols ver més es pot fer, depen de les teves necessitats.Sempre he fet "/" i "swap", i clar no més de tres, el tema del "/home" ho havia pensat per tal de no haver-el de configurar cada vegada, però no sé si faria un altre "/home"
> **wgarcia]Que no es puguin  crear més de 4 particions és una limitació històrica dels sistemes  basats en processadors Intel, els discos del qual tenien inicialment una  taula de particions que sols permetien 4. En poder fer una lògica i  aquí posar tantes com es vulguin en realitat no hi ha limitació al  nombre de particions, sols que no poden haver-hi més de 4 primàries.           [/QUOTE] Merci company!
[QUOTE=akyra said:**
> De fet si vols pots mirar aquí, [http://es.wikipedia.org/wiki/Partici%C3%B3n_de_disco.]("http://es.wikipedia.org/wiki/Partici%C3%B3n_de_disco")

M'ho miro gràcies!.


Salut!

---

### Post by akyra on 2011-03-10
Crec que les tres particons bàsiques i que s'han de fer són "/", "swap" i "/home", amb la partició "/home" evitas perdre les dades si has de instal·lar de nou el sistema operatiu, així sempre tens separades el sistema i les dades que té cada usuari.

Suposo que tu ho deus tenir el /home fet en la mateixa partició que el "/", si és així i vols instal·lar, per exemple, el ubuntu 11.04 fent una instal·lació neta, perdràs les dades.

Salutacions.

---

### Post by Funk'u on 2011-03-11
> **akyra said:**
> 
Suposo que tu ho deus tenir el /home fet en la mateixa partició que el "/", si és així i vols instal·lar, per exemple, el ubuntu 11.04 fent una instal·lació neta, perdràs les dades.
Si, exactament, em sembla que amb la pròxima versió ho faré com dius, fa temps que ho penso, però si et canvia l'entorn gràfic que passa amb la configuració?, per exemple que ho tinguis configurat per Gnome hi n'hi posin un altre.

El primer cop cap problema, però llavors com aprofites el "/home" en un altra versió?, m'hauré de mirar manuals.

Gràcies, salut!

---

### Post by wgarcia on 2011-03-12
Penso que no passa res, de fet a la mateixa instal·lació pots tenir configurat que a la pantalla d'inici puguis triar entre KDE i Gnome, per exemple, i cadascú té els seus fitxers de configuració al teu /home sense conflicte.

---

### Post by Funk'u on 2011-03-12
Mira ara precisament hauré d'instal·lar el SO a un portatil vell amb 1Gb de ram i amb tarja integrada i sense acceleració 3D, he pensat en Xubuntu (o l'Ubuntu per defecte amb un altre escriptori, alguna alternativa millor?), i ho faré amb el "/home" a part.

I dic jo, si més endavant li poses una nova versió i respectes la partició "/home", no et posa igualment un "/home" dins "/"?, o potser al veure aquest, ja no el posa i el fa servir?, perdona l'ignorància, però mai m'hi he trobat.





Salut!

---

### Post by wgarcia on 2011-03-13
Sempre i quan el /home estigui en una partició separada (tot i que la partició "/" on està tot el sistema i la partició "/home" on estan les teves dades, comencin les dues per "/", estaran en particions separades) podràs compartir /home entre instal·lacions diferents, fins i tot entre distribucions diferents si vols (un Fedora, un Debian i un Ubuntu, per exemple). Òbviament es poden produir petits conflictes, per exemple si fas servir Firefox en diferents versions i canvien una mica els fitxers de configuració d'usuari.

---

### Post by Funk'u on 2011-03-14
> **wgarcia said:**
> Sempre i quan el /home estigui en una partició separada (tot i que la partició "/" on està tot el sistema i la partició "/home" on estan les teves dades, comencin les dues per "/", estaran en particions separades) podràs compartir /home entre instal·lacions diferents, fins i tot entre distribucions diferents si vols (un Fedora, un Debian i un Ubuntu, per exemple). Òbviament es poden produir petits conflictes, per exemple si fas servir Firefox en diferents versions i canvien una mica els fitxers de configuració d'usuari.


Ho tindré en compte, moltes gràcies!




Salut!

---

