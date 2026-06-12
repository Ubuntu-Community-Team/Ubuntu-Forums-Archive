---
title: "Dues gràfiques nvidia al sistema"
date: 2010-09-13
forum: Catalan Team
---

### Post by dmartinez116 on 2010-09-13
Hola, bon dia, tinc dues gràfiques al sistema, ambdos nvidia, una 8500GT i una 8600GT, no son SLI, ni res d'això...

Les tinc perque així és més còmode tindre els dos monitors, la TV i el projector connectats a l'hora i no haver de canviar cables cada vegada....

La configuració que m'agradaria aconseguir seria:
NVIDIA 8500gt (sortida 1) --> Monitor 1
NVIDIA 8500gt (sortida 2) --> TV 42''
Estos dos dispositius haurien de funcionar com a un sol monitor (s'haurien de clonar) per a poder fer servir el pc de taula com a centre multimedia i vore'l tombat al silló... jejeje

NVIDIA 8600gt (sortida 1) --> Monitor 2 (l'utilitze junt amb el Monitor 1 com a escriptori, de manera que puga passar finestres del Monitor 1 a l'altre, etc...)
NVIDIA 8600gt (sortida 2) --> Projector (l'utilitze molt poc... i seria per a configurar-lo com a extensió (3r escriptori)

El tema és que no se que és millor... fer servir els drivers que em proposa l'ubuntu (current), el 173... o que els baixe d'nvidia i els instal·le jo. He provat amb els current i de repent el ratolí no feia clic correctament, ho minimitzava tot i ja torna a funcionar... no se... coses rares...

M'agradaria si és posible que funcionaren els 4 dispositius. A més si és posible també estaria be poder activar el cub, i les funcionalitats extra d'aparença (encara que això últim no és imprescincible)

Gràcies.

---

### Post by dmartinez116 on 2010-09-14
Be, m'he decidit per instal·lar els recomants per ubuntu (current)

I ja tinc operativa la 8500 GT, amb extres d'aparença inclosos... però ara al gestor de monitors d'nvidia... no apareix la 8600 gt, com si no hi estiguera...

ahi vos deixe el lspci per a que vegeu que està ben instal·lada al sistema:
```

lspci |grep VGA
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
06:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)

```

Amb el portàtil s'havia de canviar alguna cosa al /etc/X11/xorg.conf, però ara mateix el tinc així:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

Gràcies.

---

