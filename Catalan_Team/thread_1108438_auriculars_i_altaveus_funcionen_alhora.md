---
title: "auriculars i altaveus funcionen alhora"
date: 2009-03-27
forum: Catalan Team
---

### Post by jinglada on 2009-03-27
Al connectar els auriculars no es desconnecten els altaveus. Porto 2 dies mirant per tot arreu i no trobo la solució.

A veure si el que poso a continuació us serveix per ajudar-me

joan@joan-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

joan@joan-laptop:~$ asoundconf list
Names of available sound cards:
Intel
HDMI

joan@joan-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC662 rev1

al final de /etc/modprobe.d/alsa-base, hi tinc:
options snd-hda-intel model=6stack-dig position_fix=0

En windows vista em funciona correctament.

Si us cal alguna altra informació, feu-m'ho saber.

Gràcies a la bestreta.

---

### Post by PatrickVogeli on 2009-03-28
alla on hi tens posat model=6stack-dig position_fix=0 hi pots probar altres models, tots els que tens a continuacio.

Jo tinc un fujitsu (no amb el mateix codec que tu) i em funciona més d'un model, entre d'elles una per un benq i una d'un sony. Curiosament la de fujitsu no.

```

ALC662/663
==========
  3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  auto		auto-config reading BIOS (default)

```

Ah, provar aixo es bastant pal, perque has de rectificar la linia que tens amb el model=nou que vulguis (sense el position_fix) i reinicar la maquina, i fer-ho per a tots els models. Però bé, es molt possible que algun et funcioni.

salut i sort!

---

### Post by jinglada on 2009-03-28
> **PatrickVogeli said:**
> alla on hi tens posat model=6stack-dig position_fix=0 hi pots probar altres models, tots els que tens a continuacio. ... salut i sort!

Gràcies PatrickVogeli. Acabo d'arribar del mercat on m'han ofert loteria i no n'he comprat i ara em sap greu perquè avui deu ser el meu dia de sort. He provat el **lenovo-101e**	sense treure **position_fix** perquè no m'havia fixat amb el que tu deies > (sense el position_fix) i m'ha funcionat a la primera.:o:confused:=D>:oops: etc. etc.

Què vol dir **position_fix**? L'he de treure?

---

### Post by albandy on 2009-03-28
has provat amb el jack sensor (algunes plaques de so ho porten)?  l'has d'activar a preferencies del mixer, un cop seleccionat t'apareixerà una nova pestanya amb el nom de commutadors.

---

### Post by jinglada on 2009-03-28
> **albandy said:**
> has provat amb el jack sensor (algunes plaques de so ho porten)?  l'has d'activar a preferencies del mixer, un cop seleccionat t'apareixerà una nova pestanya amb el nom de commutadors.


És això el que vols dir? Tant abans d'anar bé com ara, sempre he tingut la pestanya commutadors amb Headphone activat.

[IMG]http://ubuntuforums.org/picture.php?albumid=1000&pictureid=3589[/IMG]

---

### Post by PatrickVogeli on 2009-03-28
Sobre el position_fix, tret de la documentacio del kernel 2.6.29
> 
DMA-Position Problem
~~~~~~~~~~~~~~~~~~~~
The most common problem of the controller is the inaccurate DMA
pointer reporting.  The DMA pointer for playback and capture can be
read in two ways, either via a LPIB register or via a position-buffer
map.  As default the driver tries to read from the io-mapped
position-buffer, and falls back to LPIB if the position-buffer appears
dead.  However, this detection isn't perfect on some devices.  In such
a case, you can change the default method via `position_fix` option.

`position_fix=1` means to use LPIB method explicitly.
`position_fix=2` means to use the position-buffer.  0 is the default
value, the automatic check and fallback to LPIB as described in the
above.  If you get a problem of repeated sounds, this option might
help.

In addition to that, every controller is known to be broken regarding
the wake-up timing.  It wakes up a few samples before actually
processing the data on the buffer.  This caused a lot of problems, for
example, with ALSA dmix or JACK.  Since 2.6.27 kernel, the driver puts
an artificial delay to the wake up timing.  This delay is controlled
via `bdl_pos_adj` option. 

When `bdl_pos_adj` is a negative value (as default), it's assigned to
an appropriate value depending on the controller chip.  For Intel
chips, it'd be 1 while it'd be 32 for others.  Usually this works.
Only in case it doesn't work and you get warning messages, you should
change this parameter to other values.


D'això jo trect amb el 0 no fas res. Seria questió de probar-ho, si no et va, sempre el pots tornar a afegir i ja esta.

Respecte al que et diu l'albandy, hi ha models de tarja que al menu que has posa't a la captura de pantalla, et surt la opció de jack sense, que es el que detecta quan hi connectes uns auricular o el que sigui i te'ls activa i et desactiva els altaveus del portatil. Si el teu no ho té, doncs res. El meu tampoc ho té.

salut!

---

### Post by jinglada on 2009-03-29
> **PatrickVogeli said:**
> Sobre el position_fix, tret de la documentacio del kernel 2.6.29
D'això jo trect amb el 0 no fas res. Seria questió de probar-ho, si no et va, sempre el pots tornar a afegir i ja esta.

Pel que dedueixo de la documentació el 0 ve per defecte. L'he tret i funciona igualment.

PatrickVogeli, moltes gràcies pel teu ajut.

---

