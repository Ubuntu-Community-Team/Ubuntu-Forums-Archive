---
title: "Error d'inici despres d'instal·lació"
date: 2016-03-30
forum: Catalan Team
---

### Post by Xavi_Brocas on 2016-03-30
Bon dia a tothom,

Fa pocs dies vaig descarregar a un pendrive i instal·lat al meu portàtil l'ubuntu 15.10. Després de realitzar la instal·lació (en principi sense cap problema), surt un missatge que em diu que he de reiniciar el sistema, en fer-ho el sistema comença normal fins que m'apareix la pantalla en negre amb el missatge: *"No bootable device insert boot disk and press any key" *i no me’n surto. La opció d'arrancada de bios es disc dur. Si intento arrencar el sistema de nou amb el USB em torna a donar la opció de provar ubuntu, instal·lar-lo o comprovar el disc (cosa que he fet i no em dona cap error). La veritat es que ja no se cap a on tirar.

Espero que algú em pugui ajudar.

Moltes gracies,
Xavi

---

### Post by wgarcia on 2016-03-30
Té pinta de ser un problema relacionat amb on s'ha ficat els sistema d'arrencada. Te'n recordes quines opcions vas escollir a la instal·lació? Els ordinadors moderns utilitzen un sistema substituïu del BIOS que portaven abans que es diu UEFI. Per arrencar aquests sistems, l'Ubuntu s'ha d'instal·lar a una partició que es diu EFI, i no al MBR del disc (Master Boot Record) com es feia abans. L'instal·lador t'hauria d'haver donat l'opció d'instal·lar l'arrencada a aquesta partició especial.

---

### Post by Xavi_Brocas on 2016-03-30
Bona tarda,

La veritat es que no recordo ben be pero crec qur vaig escollir la opció de formatejar, no recordo ben be res de cap particio.
Es possible que reinstalant el sistema en aquesta particio funcioni?
Moltes gracies per la resposta!

---

### Post by wgarcia on 2016-03-30
Sí, certament és una opció, i prestar atenció al moment que et demana on instal·lar l'arrencada, no recordo exactament com ho demana però crec recordar que és un dels primers passos.

Però potser abans seria útil que iniciessis el sistema amb un USB o CD autònom (el d'instal·lació d'Ubuntu), iniciessis una sessió de prova, i executessis el programa "gparted". Aquest programa et mostrarà quines particions hi ha ara mateix al teu disc. 

Si no ho veus clar, enganxa una captura de pantalla o una foto del que et mostra el programa "gparted".

---

### Post by Xavi_Brocas on 2016-03-30
Ara mateix per no se quin motiu no puc adjuntar una captura ni foto, pero et dire el que em surt

1. /dev/sda1  fat32  4,39MiB de 507Mib disponibles i a flags posa boot
2. /dev/sda2  ext4   15,40GiB de 675 GiB disponibles
3. /dev/sda3  linux swap  0B de 7,43GiB disponibles

Espero que et serveixi.

Moltes gracies

---

### Post by wgarcia on 2016-03-31
D'acord, el que tens a 1. sembla la partició /boot/efi, és en aquesta partició que hauries d'instal·lar l'arrencada de l'ubuntu, i no al MBR del disc. Mira de reinstal·lar a veure si veus l'opció d'instal·lar aquí l'arrencada.

---

### Post by Xavi_Brocas on 2016-03-31
D acord suposo que et refereixes a marcar /dev/sda1 com a dispositiu on isnstal&#8226;lar el carregador?
Pero despres en intentar fer-ho em diu que no s'ja definit el sistema de fitxers arrel i d' aqui no en surto.

---

### Post by wgarcia on 2016-03-31
No exactament. A la instal·lació, hi ha un moment que et deixa escollir entre deixar que el programa d'instal·lació faci la partició o fer-lo manualment. S'ha de escollir fer-lo manualment, i aquí et donarà opció d'escollir on posar l'arrencada, l'arrel, el home separat si vols, etc.

---

