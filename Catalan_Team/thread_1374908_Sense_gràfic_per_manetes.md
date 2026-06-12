---
title: "Sense gràfic per manetes"
date: 2010-01-07
forum: Catalan Team
---

### Post by farigola on 2010-01-07
Hola,

Voldria saber si algú de vosaltres podria saber com recuperar el meu KDE.
Aquesta és la configuració del meu equip i tot seguit el problema

kubuntu 9.10
Equip PC Pentium IV
4GB ram
vídeo ATI Radeon 4870 1GB

Vaig intentar millorar la qualitat de vídeo/imatge del meu equip tot pensant que amb drivers no oficials podria millorar la resolució, però la vaig pifiar i utilitzant drivers de repositoris no oficials vaig deixar l'equip sense (finestres). 
He intentat fer de tot, però no aconsegueixo recuperar el meu KDE.

Vaig procedir amb:
sudo aptitude remove xserver-xorg i tot seguit
sudo aptitude install xserver-xorg 

He fet també sudo dpkg reconfigure xserver-xorg
però res de res l'equip queda amb el login d'usuari i llestos.

No tinc idea de com seguir i recuperar el meu escriptori 
perdoneu el meu poc coneixement i potser fins i tot la manera de procedir.

Gràcies per la vostra ajuda

atentament,
Jordi.

---

### Post by lpargemi on 2010-01-07
Hola Jordi, 

Jo amb desastres similars el què havia fet és: 

1. Arrencar amb un live-cd
2. Copiar a algún lloc (un pen-drive, al disc (és més complicat perquè d'entrada no tenia permís per fer-ho), etc el fitxer /etc/X11/xorg.conf que hi ha als directoris de sistema de l'arrencada amb live-cd
3. Substituir el xorg.conf destrossat (prèvia copia de seguretat canviant el nom, per exemple) i arrencar de nou sense live-cd.

Així me n'havia sortit

Salut

Lluís Pujol

---

### Post by farigola on 2010-01-07
Hola Lluís,
he fet diferents proves doncs he vist la tira d'anotacions al web per problemes similars, he fet un **sudo aptitude install xserver-xorg-video radeon** sense resultat positiu al igual que **xserver-xorg-video-ati** 
Via cmd he fet un ls del directori per veure que dincs de /etc/X11 tenia diferents fitxers xorg.conf per data he fet una backup de l'actual i tot seguit una copia de l'anterior i al reiniciar el tema ha quedat solucionat.
Coses.;)
Gràcies i fins la propera.

---

