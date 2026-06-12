---
title: "Servidor de Dominio en Pentium 166Mhz"
date: 2007-10-07
forum: Argentina Team
---

### Post by gpone on 2007-10-07
Hola gente mi pregunta es la siguiente: ¿que distro y version de linux tengo que usar para instalar un servidor de dominio en un pentium 166Mhz? Los usuarios que se conectaran al servidor funcionan en WinXP ¿que programa tengo que istalarle para poder acceder al servidor con el WinXP?
Bueno gente muchas gracias y espero que me puedan contestar.

---

### Post by faktorqm on 2007-10-08
hola, yo te aconsejaria que mandes ubuntu server, sin interfaz grafica, y el dominio lo levantes con samba tranquilo. si necesitas algo mas avanzado avisa. sino, si necesitas algo chico chico un slackware "pelado" y samba.
no t olvides de revisar el iptables. salu2!

---

### Post by jpmorelli on 2007-10-08
Dominio o Grupo de trabajo ? En Linux existe ? O sea, compartí máquinas estilo workgroup, pero que s evaliden contra un dominio, nunca, o se puede hacer ?

---

### Post by leandr0f on 2007-10-08
> **faktorqm said:**
> hola, yo te aconsejaria que mandes ubuntu server, sin interfaz grafica, y el dominio lo levantes con samba tranquilo. si necesitas algo mas avanzado avisa. sino, si necesitas algo chico chico un slackware "pelado" y samba.
no t olvides de revisar el iptables. salu2!

 Yo estoy en la misma:confused:... y cómo armo un dominio? necesito armar la red, un Pentium200 sería el Server y se conectarían unos XP. Hace poco que estoy con Ubuntu, así que necesito mucha ayuda!

Desde ya ***Muchas Gracias!!!***

---

### Post by faktorqm on 2007-10-09
> **jmorelli said:**
> Dominio o Grupo de trabajo ? En Linux existe ? O sea, compartí máquinas estilo workgroup, pero que s evaliden contra un dominio, nunca, o se puede hacer ?

hola, si se puede, y tenes varias combinaciones posibles. no se trata de si existe o no creo yo, creo que se trata de que si m$ lo permite o no xD
como concepto digamos no se quien fue el creador, pero bueno, los que estamos en el tema sabemos muy bien por que habia que usar novell netware con nt 4........ cof cof :P
Podes tener 4 combinaciones: todo en linux, todo en m$, server en m$ y terminales linux, server en linux y terminales en m$. 
para cualquiera las 3 combinaciones que incluyen linux, hasta lo que yo se, hay que usar samba.
samba funciona como pdc, bpc o adc. pero tiene varios problemas. por ejemplo, para hacer un bpc con un pdc en m$, cuando replicas el de samba no lo puede hacer. y asi varias cosas, si tenes script's de logueo en m$ obvio que las policies no corren en linux, la verdad todavia no pude implementar nada mas que restringir desde el mismo linux al user, el otro dia lei por ahi en algun post que alguien lo hacia para que pueda ver la lectora, o algo de eso. pasen y posteen manga de gatos!

para armar la red, primero lo de siempre, defini la red, los ip's, los puertos que vas a usar, quien comparte internet, etcetcetc y despues instalate samba con apt-get install samba.

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

en esa dire tenes como levantar un pdc con samba. si necesitas algo basico basico yo escribi un tuto de samba para principiantes, pero obviamente es para compartir carpetas asi no mas, no es nada de esto.
fijense bien que quieren hacer, como, y lo vemos. salu2!!!!

---

