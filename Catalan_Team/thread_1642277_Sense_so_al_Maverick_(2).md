---
title: "Sense so al Maverick (2)"
date: 2010-12-10
forum: Catalan Team
---

### Post by Picarona on 2010-12-10
Hola a tots,

Ja fa dies que segueixo [el missatge]("http://ubuntuforums.org/showthread.php?t=1599009") del company *Quepotser* perque em trobo amb el mateix problema: tot funciona bé però no hi ha so.

He provat gairebé tot el que li heu suggerit i res de res.

Us deixo el lspci:

lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

No sóc massa de trastejar amb el terminal, fins ara no havia tingut problemes i l'ordinador que tinc (apedaçat, de peces velles) ja m'està bé per treballar i navegar. 

Si em podeu donar un cop de mà us ho agraïré molt. Salut!

---

### Post by wgarcia on 2010-12-10
Entra en una terminal la següent instrucció:

aplay -l

i mostra la resposta que et dóna.

---

### Post by Picarona on 2010-12-11
Hola wgarcia i gràcies per intentar ajudar-me.
La informació que m'has demanat:


**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by wgarcia on 2010-12-12
Prova d'obrir una terminal (Aplicacions -> Accessoris -> Terminal) i entrar el següent:

amixer set IEC958 mute

i ara intentar reproduir algun arxiu de so. No és una solució permanent però això determinarà si el problema ve del canal IEC958 que alguns diuen que causa problemes al teu tipus de targeta.

---

### Post by Picarona on 2010-12-13
Hola de nou!

Segueix sense sentir-se res. A l'introduir al terminal el que m'has dit, m'ha retornat això:

amixer set IEC958 mute
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]


Alguna idea més? :(

---

### Post by wgarcia on 2010-12-13
Prova les següents instruccions, i desfes-les després si no funcionen:


1) Mira en "Preferència de so" (clicant a la icona de so, l'altaveu, al panell superior), en "Hardware" (no sé com està traduït en català, potser "maquinari"?) i mira si tens alguna opció de fixar "Analog surround", per exemple Analog Surround 4.0 Output, si la tens, escull-la. 

2) Obra una terminal, escriu "alsamixer" i assegura't que els volums estan donats a Master, PCM, Surround, Center i LFE.

3) Agrega unes línies a l'arxiu de configuració d'alsa. Des d'una terminal:

```
sudo nano /etc/modprobe.d/alsa-base
```

Agrega aquesta línia:

```
options snd-intel8x0 ac97_quirk=3
```

4) Reinicia l'ordinador.

---

### Post by Picarona on 2010-12-14
Hola de nou.

Res, segueix sense sentir-se res de res :(
Estic per formatejar i tornar al Lucid Lynx....

Alguna idea més? (i gràcies per la paciència!)

---

### Post by wgarcia on 2010-12-17
Un altre suggeriment que he vist relacionat amb la teva targeta de so és obrir l'alsamixer en una terminal, i posar-li "Mute" a l'amplificador extern (External Amplifier) a veure si això fa alguna diferència.

---

### Post by ffp on 2010-12-17
Hola,
Jo hem vaig trobar en un cas semblant, la meva targeta es Nvidia, es va resoldre reinstalant tots els paquets alsa per synaptic i reiniciant.

---

### Post by wgarcia on 2010-12-21
Avui hi ha unes actualitzacions del nucli que incorporen avenços al mòdul del sistema de so ALSA. Prova si s'arregla amb aquesta actualització, i si no potser convindria obrir un error contra ALSA de Maverick. Si fes falta podem repassar després com es fa.

---

