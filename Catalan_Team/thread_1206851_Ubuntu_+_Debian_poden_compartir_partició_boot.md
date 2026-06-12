---
title: "Ubuntu + Debian poden compartir partició /boot?"
date: 2009-07-07
forum: Catalan Team
---

### Post by Pablitus on 2009-07-07
Hola!

En un mateix ordinador amb diferents sistemes, per exemple un ubuntu i un Debian, es poden instal·lar tots dos compartint la mateixa partició /boot?

La idea és que si un dels sistemes actualitza el kernel però al grub es carrega el menu.lst de l'altre, el nou kernel no apareix al grub en engegar l'ordinador. Fins ara ho he anat actualitzant a mà, però volia saber si hi ha una manera més ... automàtica, i s'he m'ha acudit que potser podien compartir tots dos una mateixa partició /boot. És viable? Hi ha alguna manera més "normal" d'aconseguir això?

Gràcies!!

No havia buscat prou bé. Just després d'engegar el fil he trobat [això]("http://eddiedean.wordpress.com/2008/03/15/multiarranque-en-linux/"). Hi diu ben clar que NO i encara no m'ho he acabat de llegir però crec que explica com fer el que buscava fer. Fins aviat.

---

### Post by PatrickVogeli on 2009-07-07
el que pots fer es enllaçar un grub darrere l'altre. Per exemple, tenim windows a sda1, ubuntu a sda2 i debian a sda6.

El grub d'ubuntu s'instal·la a sda1 i el grub del debian l'has d'instal·lar a sda6 (grub install sda6 em sembla que es fa). Despres, al grub d'ubuntu (que sera el que arranqui amb el PC) has de crear una entrada que arranqui la particio sda6, que podria ser alguna cosa similar a aquesta (no n'estic segur però):

title		GRUB DEBIAN
rootnoverify		(hd0,5)
savedefault
makeactive
chainloader	+1

A l'arrancar aquesta entrada et portara al grub de debian, que sempre s'actualitzara.

---

### Post by Pablitus on 2009-07-07
Exacte.

És just el que explica l'enllaç que he posat en editar, però em penso que no es veu gaire: [http://eddiedean.wordpress.com/2008/03/15/multiarranque-en-linux/]("http://eddiedean.wordpress.com/2008/03/15/multiarranque-en-linux/").

És just el que buscava i ben senzill. Per instal·lar el grub a cada partició, però, dóna una altra instrucció, entrant a un interpret d'ordres del grub:> $ sudo grub

grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit

Aquí hi ha un exemple de com quedaria el menu.lst del grub instal·lat a l'MBR: [http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html]("http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html")

PD: Ja no es poden marcar els fils com a [SOLVED]?

Fins ara!!

---

