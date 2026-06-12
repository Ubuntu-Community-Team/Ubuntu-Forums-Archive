---
title: "Grub 2, realment esta per defecte?"
date: 2009-11-09
forum: Catalan Team
---

### Post by tanreb20 on 2009-11-09
Hola!

Fa pocs dies vaig instalar l'karmic koala, la versió definitiva que fins ara estava amb la Beta.

Quan inicia el GRUB em trobo que em posa la versió 1,97 Beta 4.

I jo em pregunto, si realment el grub 2 bé per defecte, perqué jo no el tinc? Com s'instala? He provat fent un:

```
sudo aptiude install -y grub2
```

Pero rés, segueixo amb el 1.97 Beta 4... Que puc fer per instalar-ho?

---

### Post by papapep on 2009-11-09
GRUB2 és el nom del paquet, que no el nom de la versió del mateix. O sigui que pot estar en la versió 1.94, 2.05 o 44.45.32, però seguirà sent el GRUB2.

Si fas un:

```
sudo aptitude search grub2|grep ^i
```

podràs veure si el tens instal·lat o no. Si surt és que sí, si no és que no.

I si fas:

```
sudo apt-cache show grub2
```

et cantarà el que et dic del nom i la versió, i moltes coses més.

Per altra banda:

> sudo aptiude install -y grub2

"aptiude" no funcionarà mai, i l'opció "-y" és terriblement perillosa, ja que si l'**aptitude** et vol avisar de que va a fer algun estropici a la base de paquets tu li dius que no ho vols veure.

---

### Post by tanreb20 on 2009-11-09
Ok... sembla que está instalat...

Per no em deixa modificar-lo quan li afegeixo imatges, per exemple...

---

### Post by tanreb20 on 2009-11-09
Ja esta!

Era modificar una carpeta que no sé perqué, no l'havia copiat bé.

l'arxiu ha de quedar   

```
for i in {/boot/grub,**/usr/share/images/grub**}/
```

---

### Post by RicardKp on 2009-11-09
Jo no el tinc instal·lat. Voleu dir que instal·lar-lo no pot comportar problemes, la versió que hi tinc al synaptic encara és beta. Ho sento però no m'agrada massa la idea de tenir el grub en beta. Si hi han problemes apa entra amb livecd trenca't-hi les banyes i la resta d'usuaris del pc tots cabrejats i dient que amb el güindous això no passa.

---

### Post by tanreb20 on 2009-11-11
Resta d'usuaris?¿ jeje!

Aquest pc és tan sols meu! Hi puc fer els experiments que vulgui!

Avui per exemple...he canviat el xsplash, i queda preciooooooooooos!

Apart... quan thas carregat el grub com uns 15 cops... aprens a recuperar-lo XD!

---

### Post by RicardKp on 2009-11-13
Quina sort que tens de no haver de compartir l'ordinador.

---

