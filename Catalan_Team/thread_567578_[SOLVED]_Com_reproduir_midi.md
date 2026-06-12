---
title: "[SOLVED] Com reproduir midi?"
date: 2007-10-04
forum: Catalan Team
---

### Post by Asus4 on 2007-10-04
Hola!

Fa temps tenia problemes amb els fitxers MIDI's, que no els podia reproduir. Llavors, llegint un [manual]("https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo") vaig descobrir què havia d'instal·lar per tal de poder-los sentir (timidity).

Ara puc escoltar fitxers Midi, però el que passa és que no se m'obra cap aplicació mentre sona la cançó i per tant no puc aturar la reproducció ni veure quants minuts dura...etc.
Em falta instal·lar alguna cosa?
Gràcies!

---

### Post by CarlesOriol on 2007-10-05
1. El timidity pot funcionar com un servidor midi i per tant pot ser usat per qualsevol programa:

**timidity -iA -Os**

(recorda que el cal carregar el modul sequenciador 

**sudo modprobe snq-seq**

1.2 Un cop configurat el pots usar com servei.

**sudo /etc/init.d/timidity start**

Abans et caldrà configurar-lo:

**sudo gedit /etc/default/timidity**

i on diu 

[COLOR="Red"]#TIM_ALSASEQ=true[/COLOR]
treus el començament:
[COLOR="SeaGreen"]TIM_ALSASEQ=true[/COLOR]

2. També pots usar els soundfonts de la soundblaster:

Edites:** /etc/timidity/timidity.cfg** (el CT2MGM és el font de 2Mb general midi... això et caldrà copiar-ho a ma d'un insta&#320;lador windows)

[B]#source /etc/timidity/freepats.cfg

dir /usr/share/midi
soundfont CT2MGM.SF2 order=0[/B]

---

### Post by Asus4 on 2007-10-05
He seguit els passos que m'has marcat però no funciona. Ara no sento res.
De tota manera *_he corregit_* de la manera que has dit els arxius *timidity.cfg* i *freepats.cfg*.

Poso el que em surt a la consola:

**sudo modprobe snq-seq**
> joan@joan-desktop:~$ sudo modprobe snq-seq
FATAL: Module snq_seq not found.
joan@joan-desktop:~$ 


**sudo /etc/init.d/timidity start**
> joan@joan-desktop:~$ sudo /etc/init.d/timidity start
 * Starting timidity                                                             * Starting TiMidity++ ALSA midi emulation...                            [fail] 



No sé com instalar l'arxiu CT2MGM.SF2 he intentat buscar per altres pàgines però no n'he tret l'aigua clara...

Merci!

---

### Post by CarlesOriol on 2007-10-05
Punt 1PERDÓ!!!!!

sudo modprobe **snd-seq**


El punt 2 era sols per si disposabes de soundfonts.

Deixe l'arxiu com estava:

```
# Instrument configuration file for timidity
# $Id: timidity.cfg,v 1.7 2005/09/03 19:26:03 hmh Exp $

# You can change just about every option in TiMidity++ using
# This config file.  Please refer to the timidity.cfg(5) manpage
# for more details

## If you have a slow CPU, uncomment these:
#opt EFresamp=d		#disable resampling
#opt EFvlpf=d		#disable VLPF
#opt EFreverb=d		#disable reverb
#opt EFchorus=d		#disable chorus
#opt EFdelay=d		#disable delay
#opt anti-alias=d	#disable sample anti-aliasing
#opt EWPVSETOZ		#disable all Midi Controls
#opt p32a		#default to 32 voices with auto reduction
#opt s32kHz		#default sample frequency to 32kHz
#opt fast-decay		#fast decay notes

## If you have a moderate CPU, try these:
#opt EFresamp=l
#opt EFreverb=g,42
#opt EFchorus=s
#opt s32kHz
#opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:

source /etc/timidity/freepats.cfg
```

---

### Post by Asus4 on 2007-10-08
He fet aquests dos passos corregits i torno estar igual que al principi.
Puc executar els fitxers midi però no se m'obra cap aplicació amb la qual pugui controlar-ne la reproducció. Els sento però no els puc aturar.

Què puc fer?
Merci!

---

### Post by Asus4 on 2007-10-08
Per més inri: he intentat obrir els fitxers midi amb els programes "Totem" (el reproductor x defecte d'Ubuntu) i amb el "Amarok" (un que sortia recomanat a la llista de reproductors de Midi) i cap dels dos me'ls permet reproduir.

És estrany tot plegat...:confused:

---

### Post by CarlesOriol on 2007-10-09
El mateix timidity ho permet.
També tens:
el kmid, seq24, rosegarden, muse, pykaraoke, playmidi, pmidi...

Si has iniciat el timidity com a servei fins i tot pots fer-ho amb el firefox

---

### Post by Asus4 on 2007-10-09
Merci!
De moment sembla que tot funciona, faig servir el mateix timidity. Però s'agraeix la llista de programes alternatius.

Fins aviat!

---

