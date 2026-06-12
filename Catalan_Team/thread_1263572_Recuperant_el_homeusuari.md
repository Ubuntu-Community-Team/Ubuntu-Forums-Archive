---
title: "Recuperant el /home/usuari"
date: 2009-09-11
forum: Catalan Team
---

### Post by Mitsurugi on 2009-09-11
Hola a tothom, us explico la meva batalleta del 11-S espero que no perduda, a veure si em podeu ajudar.

He googlejat una mica hi he trobat quelcom semblant, però diria que no és el mateix [http://ubuntuforums.org/archive/index.php/t-1165417.html](http://ubuntuforums.org/archive/index.php/t-1165417.html)

M'he llevat amb les actualitzacions de programari nou kernel tal, reinicio i pataplam! Kernel Panic

Fico un liveCD, comprovo que els arxius es mantenen, i decideixo fer una nova insta&#320;lació a /

Originalment tenia

```

/dev/sda1  /  (12 GB)
/dev/sda2  /swap (2GB)
/dev/sda3  /home (150GB)
```

Evidentment, vull mantenir la part del **/home/mitsu** on i tinc tots els arxius així que unicament, refaig el **/dev/sda1** formatant-lo i dient-li que sigui el **/** altre cop

Fins aquí perfecte, fico l'usuari, la contrasenya, etc ...

I entro al sistema, el primer que faig és dirigirme al** /home/mitsu** altre cop i me'l trobo buit, ](*,)

Calma't, veig que hi ha una partició de 150GB, la munto 

i veig que es tracta de **/dev/sda3** en **/media/disk**

uuuuuuuuuf \\:D/

Bé, els arxius hi son, problema? Vull que **/media/disk/mitsu** torni a ser **/home/mitsu**

Però no puc simplement copiar els arxius d'un lloc a l'altre, per què el nou /home/mitsu es troba dins d'una partició **/ (dev/sda1**) (recordem de 12GB)

i el **/dev/sda3 en /media/disk** en son més de 60GB ja, per tant no hi cabria

Doncs això voldria tenir-ho tot com abans.

Gràcies per avançat companys.

Desconec si es necessari, però us fico l'arxiu fstab que tinc [http://paste.ubuntu.com/269054/](http://paste.ubuntu.com/269054/)

---

### Post by Mitsurugi on 2009-09-11
Bé, m'hauré de contestar ja que sembla ser que ho he solucionat

He editat el fstab i li he ficat la següent línia


```
/dev/sda3	/home	ext4	defaults	0	2
```

---

### Post by PatrickVogeli on 2009-09-11
durant la instal·lació, li havies d'haver dit de montar la particio /dev/sda3 a /home i NO formatejarla.

Salut

---

### Post by Mitsurugi on 2009-09-11
Gràcies! ho tindre en compte també la pròxima vegada :D

PS: Per cert, encara esteu de festes avui a Cambrils?

---

