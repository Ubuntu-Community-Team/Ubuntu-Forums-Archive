---
title: "configurar grub"
date: 2007-06-12
forum: Catalan Team
---

### Post by canbretxa on 2007-06-12
Soc bastant nou amb Ubuntu i m'ha sorprès que no hi hagi cap eina per configurar el gestor d'arrencada.

En coneixeu algún de programet poder fer-ho sense tenir que anar amb la consola i editar algun fitxer, cosa que hem fa pànic.

Salutacions

---

### Post by Ferri on 2007-06-12
Això em sembla que et pot anar bé:
[GUI Grub editing]("http://ubuntuforums.org/showthread.php?t=228104")

---

### Post by crazyserver on 2007-06-13
Hi ha un altra aplicació que pots usar: [Start-up Manager]("http://web.telia.com/%7Eu88005282/sum/index.html"), encara no està dins dels repositoris d'ubuntu però pots seguir això:
[Start-up manager a Cesarius Revolutions]("http://www.cesarius.net/startup-manager-gestiona-el-arranque-de-tu-sistema-ubuntulinux/")

---

### Post by telejet on 2007-06-15
Obrint un terminal (tranquil només hi escriuràs una ordre ;) ) i fent

sudo gedit /boot/grub/menu.lst

Ja tens un editor gràfic, esborres les entrades que et sobren i afegeixes les que vulguis, anant en compte és clar. Desa l'arxiu.

i ara per a què agafi els canvis fes:

sudo update-grub

I llestos.

Salut

---

