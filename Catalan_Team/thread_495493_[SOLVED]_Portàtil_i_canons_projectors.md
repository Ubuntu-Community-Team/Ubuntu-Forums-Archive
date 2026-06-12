---
title: "[SOLVED] Portàtil i canons projectors"
date: 2007-07-08
forum: Catalan Team
---

### Post by lluisanunez on 2007-07-08
Bones,
darrerament faig servir molt el portàtil amb Ubuntu a les classes, connectant amb la wifi i projectant amb els variats canons que hi ha per les aules.
Cap problema fins ara, excepte que quan connecto el cable VGA, em quedo sense pantalla, ja que tot el senyal video se'n va al projector, i jo he d'anar mirant el que es projecta a la paret. Quan pregunto als tècnics de les aules ho volen configurar amb la tecla Fn+F5 (CRT/LCD), però si es toca aquesta combinació es penja el teclat.
Amb versions anteriors de linux i aquest mateix portatil havia aconseguit configurar el display amb 'doble cap', però ara el gnome només em permet canviar la resolució, no el tipus de monitor, i no tinc ni idea de com canviar això al Xorg.conf
Si sabeu la solució m'estalviareu algunes tortícolis :(

---

### Post by CarlesOriol on 2007-07-08
qquina gràfica tens?

---

### Post by lluisanunez on 2007-07-08
Intel 82852/855GM

---

### Post by papapep on 2007-07-08
Jo tinc un Ibm Thinkpad R50e amb aquesta mateixa gràfica i em va correctament. Com a mínim a la Festa Feisty va funcionar, com tu dius, de manera bicéfala :-)

---

### Post by CarlesOriol on 2007-07-09
Cerca informació detallada de la 915.

Jo tinc una intel en un mediacenter i vaig haver de fer un bon remix de xorgs.

Mira:

```
        Option  "VBERestore" "yes"
        Option  "Clone" "true"
        Option  "MonitorLayout" "CRT,LFP"
        Option  "DevicePresence" "yes"

```
de  [http://ubuntuforums.org/showthread.php?t=415776](http://ubuntuforums.org/showthread.php?t=415776)

---

### Post by lluisanunez on 2007-07-09
Ok, moltes gràcies, provo (quan tingui un projector a mà)

---

### Post by orestesmas on 2007-07-11
Bé, no sé perquè et desapareix la imatge del portàtil, però sí que sé perquè es penja en fer Fn+F5. Això també em passava a mi en un portàtil de la feina que té una gràfica intel i, encara que soni una mica fort, és culpa d'un bug del controlador intel de les xorg. Més fort encara, jo ho vaig solucionar baixant-me les fonts del driver, aplicant un pedaç i recompilant el driver. No m'ho creia però va funcionar de meravella. A banda d'això, els passos a seguir no són massa complicats.

D'altra banda és un bug confirmat. Tota la info és aquí:
[https://launchpad.net/ubuntu/+source/xserver-xorg-driver-i810/+bug/50243](https://launchpad.net/ubuntu/+source/xserver-xorg-driver-i810/+bug/50243)

Si tens alguna dificultat en el procés, digues-ho.
Sort.

---

### Post by lluisanunez on 2007-07-11
Interessant! ja ho sospitava, de fet aquest bug era més gros amb versions anteriors de X: no em funcionava cap dels botons Fn (ara aquest és l'únic que no va)
Em llegeixo la solució a veure si la sé posar en pràctica però m'hauré d'esperar a les vacances: el portàtil amb l'Ubuntu em funciona tan bé, es connecta a les wifis de les facultats com una seda, sempre funciona a les presentacions, i a tot arreu provoca preguntes sobre el programari lliure :-) ... que no m'atreveixo a tocar-ho ara.
Moltes gràcies!

---

### Post by lluisanunez on 2007-08-08
Solucionat! Amb les modificacions a xorg.conf que em proposaves, CarlesOriol.
Què feliç que sóc podent mirar la meva pantalla mentres la projecto pel canó :guitar:

Moltes gràcies

---

### Post by migjorn on 2007-09-26
hola a tothom!
Jo tinc el mateix problema. No puc veure el la pantalla del projector i la de l'ordinador alhora. 
Tinc (crec, perquè no ho sé segur), una NVIDIA GeForce Go 7600). També hauria d'editar l'arxiu del Xorg de què parleu? Com ho faig?

Moltes gràcies!

---

### Post by papapep on 2007-09-26
Migjorn, el post que havies fet abans l'he tret d'aquest fil i n'he creat un de nou a fi de que separem temes amb diferent solució.
El fet que sigui una targeta gràfica no significa que ho puguis solucionar igual :-)

El trobaràs aquí:

[http://ubuntuforums.org/showthread.php?t=560441](http://ubuntuforums.org/showthread.php?t=560441)

Segueix allà, si us plau.

---

### Post by migjorn on 2007-10-01
Gràcies, Papapep. Però el cas és que ningú no m'ha respost encara...
Algú em pot fer un cop de mà, sisplau?

Salut!

---

### Post by dvdgmz on 2007-10-04
Hola,
Em passa algo semblant (o pitjor).
En general no em funciona el portàtil ni amb projectors ni amb aparells de televisió. Ni connectant el cable VGA ni amb altres sortides que té de Vídeo compost o similar.
Però si arrenco primer Windows (quasi el tinc per això:) ) amb el cable connectat i després re-inicio amb Ubuntu llavors si que ho "pilla".
Això sí, passa el que dieu, només es veu al Projector (o TV), desapareix de la pantalla del portàtil.
Tampoc veig com fer servir dues pantalles pel mateix escriptori (amb Windows puc).

Portàtil:
ASUS A5EC

Tarja gràfica:
INTEL 915GM
(crec, ho diu un adhesiu que porta l'ordinador, suposo que ho hauria de mirar a Gestió de Dispositius però allà hi ha un fotimer de coses difícils d'entendre :( )

Sistemes:
Ubuntu-6-Dapper
Windows XP Home Ed.

Com migjorn pregunto, què és això de Xorg i com l'hauria d'editar?

Salut.

dvd.

---

### Post by papapep on 2007-10-04
Nois, no és per res, però al fil que es va crear per parlar d'això en concret han contestat i ningú s'ha donat per aludit. 
Aquest fil on som ara ja està resolt, seguiu a l'altre o la cosa no funcionarà com cal.

[http://ubuntuforums.org/showthread.php?t=560441](http://ubuntuforums.org/showthread.php?t=560441)

---

