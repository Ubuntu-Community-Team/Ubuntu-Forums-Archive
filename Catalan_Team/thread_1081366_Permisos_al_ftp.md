---
title: "Permisos al ftp"
date: 2009-02-26
forum: Catalan Team
---

### Post by socderafel on 2009-02-26
Hola a tots!
Estic tornantme loco amb els permisos d'un servidor ftp local que he montat en casa. 
He habilitat l'usuari anonymous per a que puga pujar arxius, ja que anem a gastar-lo de magatzem. 
tinc permissos asignats (777) a la carpeta ftp/pub , i em deixa fer de tot. el problema es que quan puje un arxiu desde un altre ordinador de la xarxa local, es queda sense cap permís, i una volta pujat no el puc ni obrir desde el servidor ni baixarlo desde un altre pc. 
Si faig desde el terminal sudo chmod -R 777 /ftp/pub ja els puc vore tots, pero quan puje un altre arxiu, este es crea sense permisos. 
A vore si pugueu tirar-me una maneta...

---

### Post by thedavis on 2009-02-26
Què fas servir el proftpd o el vsftpd?

---

### Post by socderafel on 2009-02-26
vsftpd

---

### Post by thedavis on 2009-02-27
Mira dins del archiu de configuració /etc/vstfpd/vstfps.conf a veure si tens habilitat:

> 
local_umask=077  #crea els directoris amb els permisos als usuaris normals
anon_umask=077  #crea els directoris amb els permisos 077 als anonims 
anonymous_enable=YES
anon_upload_enable=YES #es per que l'usuari anonim pugui pujar arxius


A veure si funciona...

---

### Post by socderafel on 2009-02-27
segueixc sense poder obrir ni descarregar un arxiu quan el puge desde anonim.
L'opció anon_umask no m'apareix per cap lloc al fitxer...
si no entre com a anonim i entre amb el nom d'usuari i contrasenya si q em deixa.
el problema sols es quan entre com a anònim...

---

### Post by thedavis on 2009-03-02
Prova de posar l'opció de totes formes, l'unic que pot passar es que quan facis el restart no t'arrenqui, en aquest cas ja sabrás perquè és. Per provar no perds res :)

---

