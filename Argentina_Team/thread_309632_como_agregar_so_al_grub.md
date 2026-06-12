---
title: "como agregar so al grub"
date: 2006-11-29
forum: Argentina Team
---

### Post by eljugado on 2006-11-29
Hola a todos soy nuevo en este mundo de so de la familia unix.
Hace poco instale el open solaris aparte del windows, luego instale el kubuntu, pero resulta que el solaris no aparece en el grub de ubuntu, el windows si. Quisiera saber cuales son los pasos para agregarlo, si alguien me puede ayudar.
Muchas gracias.
Marcos.

---

### Post by Nemesis Teufel on 2006-11-29
aaaaaaaaaaaaa no me hables de grub!!!!
me voy a volver loco!!

no, mentira. Probá con esto: [http://www.3d-arg.com/forum/linux/13663-super-disco-grub.html](http://www.3d-arg.com/forum/linux/13663-super-disco-grub.html)

---

### Post by QUASAR_FREAK on 2006-11-30
Aca te dejo un ejemplo de como deberia ser la nueva entrada en grub.conf para solaris, acordate de poner bien el dico y particion:
[FONT=monospace]
[/FONT]title Solaris
rootnoverify (hd0,0)	
makeactive
chainloader +1

---

