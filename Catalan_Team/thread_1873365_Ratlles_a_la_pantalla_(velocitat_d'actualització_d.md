---
title: "Ratlles a la pantalla (velocitat d'actualització del monitor?) a Ubuntu 11.10"
date: 2011-11-01
forum: Catalan Team
---

### Post by U-Joan on 2011-11-01
Hola!

Tenc un portàtil que m'agrada connectar a la televisió a través de HDMI. La qüestió és que amb la instal·lació d'Ubuntu 11.10 me la detecta com a Sony 65", encara que és de 46" i quan la configur a la resolució 1920x1080 perquè aprofiti tota la pantalla, qualsevol moviment encara que només sigui per desplaçar el punter del ratolí provoca que apareguin ratlles. Aquest problema no em passa amb altres resolucions, però o no aprofiten tota la pantalla i es veu a 4:3, o la imatge de l'escriptori no surt tota.

Mirant per internet sembla que aquest problema pot ser degut a la velocitat d'actualització del monitor, i en algun tutorial he vist que en versions anteriors d'Ubuntu açò era tan senzill de corregir com canviant-la a la finestra de configuració dels monitors, amb diferents opcions a 60Hz, 75 Hz, 85Hz... Però en la finestra actual de l'Oneiric Ocelot aquesta opció no sé perquè no existeix i només es pot triar la "resolució" i la "rotació". 
:(
També he vist alguns casos en què aquesta configuració de la velocitat d'actualització es pot canviar redactant unes instruccions al terminal, però també són per versions anteriors i no ho acab d'entendre, i com que no ho he fet mai no voldria esgarriar-ho i que em quedés pitjor que com està ara.

Algú em pot ajudar i dir-me si es pot canviar i com ho he de fer amb l'Ubuntu 11.10 per evitar les ratlles a la pantalla?

---

### Post by U-Joan on 2011-11-02
Com deia ahir, havia vist que amb unes instruccions al terminal es poden fer modificacions de la resolució i la velocitat de refresc de la pantalla. Avui m'hi he decidit a escriure xrandr al terminal i m'han sortit aquestes dades:

Amb el monitor del meu portàtil apareix açò:

Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x900       60.0*+
   1440x900       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)

Quan connect el portàtil amb el cable hdmi a la pantalla de la tele apareix el següent:

Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x900       60.0*+
   1440x900       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +
   1280x1024      60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  

I finalment quan desconnect la pantalla del portàtil amb les opcions de configuració de monitors per passar la imatge a la tele, m'apareix el següent:

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected (normal left inverted right x axis y axis)
   1600x900       60.0 +
   1440x900       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1440mm x 810mm
   1920x1080      60.0*+
   1280x1024      60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  

No entenc què vol dir el símbol de *+ o només + que apareix al costat del 60.0 de la resolució: es pot canviar perquè sigui superior? Com es podria fer?

A la web on m'ho mirava es diu que per canviar-ho s'ha d'editar un arxiu amb una instrucció que diu $sudo gedit /etc/gdm/Init/Default però si ho escric al terminal em surt que aquest arxiu no existeix i aquí és on estic embarrancat ara mateix.

En fi, no sé si vaig bé per resoldre el problema...

---

### Post by U-Joan on 2011-11-14
Hola de nou,

Bé, escric més que res per explicar com tenc aquest problema, que he solucionat parcialment, i per plantejar una pregunta.

No he pogut canviar les opcions de resolució ni de velocitat de refresc amb cap de les instruccions que he anat trobant per internet, però a base de fer proves m'he "topat" amb una solució que almenys em serveix. Resulta que quan connect el portàtil al televisor, si configur a monitors perquè la imatge es vegi a la tele directament a 1920x1080 i es desconnecti la pantalla del portàtil em passa el problema de les ratlles, i és en l'única opció de resolució que passa. En canvi si prèviament ho configur perquè la imatge es comparteixi tant a la tele com al portàtil (es crea un escriptori més extens) i accept la configuració, i posteriorment faig una nova configuració desconnectant la pantalla del portàtil, la imatge es manté estable.

No sempre em funciona a la primera i és una mica enredós fer-ho d'aquesta manera, però almenys ja puc tornar a gaudir del meu portàtil a tota pantalla amb Ubuntu!
 ::popcorn: :P:D

Per què passa aquest inconvenient? Si qualcú m'ho pot dir... De totes maneres seguesc tenint problemes amb la connexió HDMI, i aquí ve la segona part de la qüestió, ja que **l'àudio del portàtil no es sent amb el televisor**, només al mateix portàtil. He intentat canviar les opcions a paràmetres de so, però res. Alguna solució?

---

### Post by Frealof on 2013-01-04
Hola U-Joan,

Jo em trobo amb un problema similar, però amb una TV Sony Bravia a la qual connecto el portàtil via VGA (la targeta del portàtil és una Nvidia Geforce Go 6100).

Fins ara sempre m'havia anat bé, vaig anar canviant de versió d'Ubuntu (Des del Dapper Drake) i tot anava bé, fins ara. Que al passar a l'última estable 12.04 em trobo que, quan canvio a la TV, primer fent que es vegi l'escriptori als dos monitors i després només a la tele, el refresc no va com hauria d'anar.

Si a algú se li acud alguna solució seria d'agraïr, gràcies ;)

---

### Post by ffp on 2013-01-05
Hola,
Amb targetes nvidia, el problema de les ratlles pot ser del composite. Es pot intentar iniciar sesió sense 3d (Unity 2D)
De fet el composite es necessita per fer el 3D i l'unity. Al 12.04, es pot editar el xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
i afegir al final 
```
    Section "Extensions"
    Option "Composite" "disable"
    EndSection
```
Reiniciar i provar.

---

### Post by wgarcia on 2013-01-06
Una altra opció és provar amb diversos controladors. Si s'està usant el controlador privatiu, intentar usar per exemple el controlador lliure "nouveau". I si s'està usant el lliure, provar amb el privatiu. 

Per veure quin controlador s'està usant "Paràmetres del sistema -> Controladors Addicionals" (penso que a la versió 12.04 encara està com a opció separada, a la 12.10 està com una pestanya de "Fons de programari").

---

