---
title: "kde 4"
date: 2008-01-23
forum: Argentina Team
---

### Post by joseluis on 2008-01-23
amigos, tengo ubuntu 7.10 y estoy con ganas de meterle en entorno kde. Quisiera preguntar si saben si al instalar ese entorno ya me viene conel KDE 4.

gracias

---

### Post by anka on 2008-01-23
Uso gnome y que yo sepa no, hay que tocar el source.list para que puedas hacerlo. En google hay decenas de tutos, todos son iguales, asi que.., por que no?:

Abris el source.list con un editor de texto:

*sudo gedit /etc/apt/sources.list*

Agregas estas lineas:

*deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main*

Guardas los cambios y cerras. Luego actualizas:

*apt-get update*

E instalas KDE4:

*apt-get install kde4-core*

Al iniciar una secion con KDE deberia de anadar lo mas bien

Suerte!

---

### Post by pablo0469 on 2008-01-24
Lo que te explicaron arriba esta perfecto, pero acordate de traducirlo, sino te aparece todo in inglish:

sudo apt-get install kde-i18n-es

Saludos.

PD: esta bueno, pero es mucho mas comoda y funcional la version 3.5.8, te recomiendo que esperes un poco para la 4.

---

### Post by facundocorradini on 2008-01-24
Coincido con Pablo, KDE 4 es una versión "no-estable para producción", lo que en mi experiencia significa inusable. 

Te recomiendo instalar simplemente KDE3, pero si tenés ganas de experimentar, la  forma de instalar KDE4 que te dijo anka es la mejor.

saludos

---

### Post by joseluis on 2008-01-24
gracias..voy a esperar que salga mejor el kde4

---

### Post by pablo0469 on 2008-01-24
Es muy similar al que venia en SuSe 10.2, obviamente en ese caso mucho mas pulido, pero me resulto absolutamente poco practico e infuncional, prefiero mucho mas el clasico despliegue de menues y submenues.

Saludos.

---

### Post by anka on 2008-01-25
Me hizo acordar exactamente a eso, siempre lo criticaron porque era muy pesado.., pero de kde no se nada, repito que uso gnome.

Lo mas logico para usar KDE4 es esperar hasta la 4.1 al menos, esta muy nuevo todavia y recien se esta usando "en serio" como para ver que problemas trae.

Suerte y no sean tan impacientes :P

---

### Post by clasificado on 2008-01-26
Ajá, es cierto. Vengo usando kde4 hace un par de dias, y todavia tiene sus inconvenientes. y como tenia kde3 hay un par de configuraciones mezcladas que tendré que arreglar a mano.

Ahora, para los que quieran divertirse: plasma, solid y las nuevas versiones de qt4 son muuuuuuuuuuy buenas.

y dolphin quedo muy piola.

clasificado.

---

### Post by SLA_leandrin on 2008-01-26
Por lo que ví y leí de KDE4, no me atrae demasiado, prefiero por ahora seguir usando gnome... a pesar de que dicen q el 4 consume menos recursos que el 3.5, no me animo a usarlo en mi pobre PC de modestos recursos....

---

