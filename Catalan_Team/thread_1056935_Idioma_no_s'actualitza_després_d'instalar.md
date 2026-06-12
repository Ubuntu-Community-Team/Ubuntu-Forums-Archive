---
title: "Idioma no s'actualitza després d'instalar"
date: 2009-02-01
forum: Catalan Team
---

### Post by ritoda on 2009-02-01
Hola bona tarda

Fa ja uns mesos que al meu pare li vaig instal·lar l'ubuntu hi ha funcionat be... fins fa poc. Avui li he tingut de fer una reinstal·lació donat per si sol darrerament no se li actualitzava el sistema i apareixien alguns errors de tant en tant.

Després de l'instal·lació m'he donat compte que no ha actualitzat l'idioma a català i sembla no acaba de baixar els paquets.

Concretament dona aquest error:
W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  No s'ha pogut connectar amb es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)

A mes, no deixa afegir cap aplicació doncs el sistema vol primer  instal·lar els paquets que falten, donant de nou aquest error.

Pel demés sembla que tot funciona


Em podeu donar un cop de ma? 
gràcies

---

### Post by torracastanyes on 2009-02-01
Es possible que el servidor.es tingui problemes de connexió.
Prova-ho anant a Fonts de Programari i canvia el "servidor per Espanya" pel "servidor principal", o bé digues que et busqui el millor, a veure si així funciona.

---

### Post by Diegstroyer on 2009-02-01
Mira el que es comenta en aquest fil, potser que sigui el mateix:
[URL="http://ubuntuforums.org/showthread.php?t=1047023&page=4"]
http://ubuntuforums.org/showthread.php?t=1047023&page=4[/URL]

---

### Post by ritoda on 2009-02-01
Bones, 

a la llista d'idiomes només hi constava l'anglès i
seguint els fils que m'heu donat he arribat a fer això:


sudo aptitude purge language-pack-gnome-ca language-pack-gnome-ca-base
sudo aptitude install language-pack-gnome-ca language-pack-gnome-ca-base


el cas es que ha funcionat.

---

### Post by orestesmas on 2009-02-03
No n'hi ha prou. Cal instal·lar també, com a mínim, el paquet "language-support-ca". Aquest és el que instal·la les dependències necessàries per tenir, entre altres coses, els correctors ortogràfics de l'Openoffice en català.

---

