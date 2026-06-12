---
title: "[SOLVED] No arranca el sistema:No bootable device"
date: 2007-07-21
forum: Catalan Team
---

### Post by benetj on 2007-07-21
Hola a tothom!!
Volia comentar-vos el petit problema que tenc i que no se solventar per mi sol.

Fa uns dies me vaig comprar una placa base Intel (per més senyes es la DG965RY) amb un processador intel core 2 duo xaxiguai, 2GB de RAM i un disc dur SATA de 160GB. jeje

Vaig instal·lar al Feisty i pareixia que m'ho detectava tot be, disc SATA particionat, el so perfecte, grafica també, ...
La meva sorpresa fou quan vaig reiniciar que me va mostrar un missatge *"No bootable device -- insert boot disc and pres any key"*

A partir d'aquí vaig anar fent consultes a gent per veure si aclareixo el que passa. Vaig arrancar el sistema amb una livecd per veure si hi era tot. Es va montar perfecte. Vaig intentar fer un *grub-install /dev/sda* i me deia que no trobava res.
He canviat la informació de la BIOS, He posat el SATA com a IDE i com a AHCI i res, la veritat ja no se com fer-ho.

Moltes gràcies per llegir-me, esper una resposta , jejeje 

salut!!

---

### Post by papapep on 2007-07-21
Crec que hauries de comprovar si la partició que tinguis per a iniciar el sistema té el senyalador "boot" marcat . Fent-ho amb un live-cd i el gparted si vas a Partició > Gestiona senyaladors, podràs veure si tens marcat "Boot".

---

### Post by benetj on 2007-07-22
Buf!! mil gràcies!!!
No havia caigut amb aquest petit detall. 

Salut!!

---

### Post by papapep on 2007-07-22
O sigui que ara ja et funciona  bé?

---

### Post by benetj on 2007-07-23
Doncs si, ara arranca perfectement.
No vaig pensar a posar com a "bootable" la partició principal (/).

Gràcies!!

---

### Post by ~~Tito~~ on 2007-07-23
Oyes estan hablando espaniol? Y que es el botton de el ~ para el n?

---

### Post by papapep on 2007-07-23
> Oyes estan hablando espaniol?

Doncs no senyor, estem parlant català  [http://es.wikipedia.org/wiki/Idioma_catal%C3%A1n]("http://es.wikipedia.org/wiki/Idioma_catal%C3%A1n")

I respecte a això altre que dius: > Y que es el botton de el ~ para el n?


no entenc la pregunta.

---

### Post by ~~Tito~~ on 2007-07-23
Que? Mi familia desende de espania pero yo no entiendo el (dialogue).

---

### Post by ~~Tito~~ on 2007-07-23
> **papapep said:**
> Doncs no senyor, estem parlant català  [http://es.wikipedia.org/wiki/Idioma_catal%C3%A1n]("http://es.wikipedia.org/wiki/Idioma_catal%C3%A1n")

I respecte a això altre que dius: 

no entenc la pregunta.

Si entiendes ingles lea esto.
I dont know how to combine the ~ with the n on a english keyboard.

---

### Post by papapep on 2007-07-23
But what do you want to do with that combination?, I don't get what are you trying to do.

By the way, I don't mind, as you can see, talking in english or in any other language I know, but as this is a catalan language forum perhaps you'd better ask in an english forum so you could get more help. ;-)

---

