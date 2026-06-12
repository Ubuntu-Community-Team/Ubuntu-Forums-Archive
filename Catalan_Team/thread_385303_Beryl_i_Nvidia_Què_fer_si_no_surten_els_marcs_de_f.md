---
title: "Beryl i Nvidia: Què fer si no surten els marcs de finestra"
date: 2007-03-15
forum: Catalan Team
---

### Post by sianeu on 2007-03-15
Seguint amb el meu penós aprenentatge amb la gràfica 7600GS de Asus, tampoc no em funcionava del tot el Beryl: no apareixien els marcs de les finestres. Després d'uns quants intents frustrats he aconseguit la solució amb un manual del desaparegut blog del fred.cpp. Es molt senzill:

Obrim **sudo gedit /etc/X11/xorg.conf**

i a la secciò **Screen** afegim al final aquestes dues linies:

[B]Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"[/B]


Tambè em de mirar al final de tot del fitxer que hi tinguem (sino ho afegim) aquest apartat:
[B]
Section "Extensions"
Option "RENDER" "Enable"
EndSection
[/B]

Amb això ara ja em va perfecte.

Salut

PD: El manual es per el Edgy y a mi m'ha funcionat amb el Feisty, no se si val en altres versions.

---

### Post by vinga on 2007-05-01
Gràcies per la resposta. A mi m'ha estat de gran ajuda, Només afegint aquestes quatre línies al xorg.conf, el beryl funciona de meravella!! :popcorn:

---

