---
title: "EEE PC 1025C: No aconsegueixo configurar-la millor que a 800x600"
date: 2012-08-04
forum: Catalan Team
---

### Post by lpargemi on 2012-08-04
He instal·lat Ubuntu 12.04 en un Asus EEE PC 1025C, i no he aconseguit de cap manera que es vegi millor que a 800x600.
La pantalla és de 1024x600, però el sistema no me la reconeix, ni trobo per enlloc drivers. 
Sabeu com es podria fer?
(Per cert el mític etc/X11/xorg.conf es veu que ja fa versions que no existeix... i tampoc sé on provar de modificar...)
Agraït

Lluís

---

### Post by wgarcia on 2012-08-06
Em sembla que tens la Intel GMA 3600, per la qual el nucli de Linux que ve amb la versió 12.04 no té suport. Em sembla que els nuclis de la nova versió, la versió 12.10 (3.4) si que en tindrà. 

Per confirmar pots fer des d'una terminal:

```
lspci | grep -i vga
```

i comentar si et diu quina és la targeta gràfica d'aquest ordinador?

---

### Post by lpargemi on 2012-08-09
Gràcies pel comentari

He estat uns des fora i ara m' ho he mirat. La resposta a la comnda és:
```
:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)

```

A veure si hi ha sort i es pot fer anar.

---

### Post by kimet on 2012-08-09
Escriu xrandr al terminal, et donara les resolucions disponibles.
Si apareix la que tu vols, executa:
```
xrandr --output VGA1 --mode 1024x600
```
On VGA1 es el nom del monitor que apareix al executar xrandr.

Et pot donar una idea de si funciona o no.

Salut.

---

### Post by lpargemi on 2012-08-09
He provat això d'xrandr, i només té 800 x 600

he provat una altra cosa: el què diu aquí [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239"), i més concretament amb el què diu aquí: [http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/]("http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/"), amb resultat de mort...

Ara ja no va res, s'engega, veig lletres que corren durant l'arrencada, i s'apaga i ja no va mai més. Si teclejo el password fa alguna cosa més (el llum del disc) però no funciona més.

Provaré d'editar de nou el grub i treure aquesta opció denl video... o caldrà tornar al costat fosc?

---

### Post by lpargemi on 2012-08-09
No sé com accedir al grub. Arrencant des d'un live-cd en usb no tinc accés ni permís ni tan sols per veure'l.

---

### Post by lpargemi on 2012-08-09
Al final sembla que me n'he sortit. Des d'un live CD he pogut trobar el fitxer grub bo (que apareix dins de "media" amb una identificació un pel estranya, que suposo que correspon al disc). Amb un sudo he pogut desfer els canvis que hi havia fet, però no ho l'he pogut compilar.
He arrencat, a les fosques he entrat el passwortd, obert un terminal (Ctr+Alt+T), he compilat el grub (sudo update-grub-2) i quan el disc s'ha aturat he tancat la màquina.
I com per art de màgia quan ha tornat a arrencar no només he recuperat la gràfica, sino que ho ha fer a la resolució de 1024x600.

Bé, segurament hi ha una manera menys erràtica de fer-ho, però així ha funcionat.

Gràcies a tots.

---

### Post by wgarcia on 2012-08-11
Que bé que s'hagi arreglat, tot i que llàstima que no hagi quedat clar com.

---

### Post by lpargemi on 2012-08-11
Teniu raó, miro d'explicar-me millor.

Amb la instrucció ```
:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
```
Vaig saber veure quina mena de targeta de vídeo hi havia. Buscant a google "*Intel Corporation Atom Processor D2xxx/N2xxx*" vaig trobar una pregunta de launchpad, aquesta [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239"), on hi havia unes respostes d'en Josep Pujades apuntant a un segon enllaç on explicàven la forma de solucionar-ho. L'enllaç és aquest: [http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/]("http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/").

La solució que proposen, pel què penso entendre, consisteixen en fer servir un kernel determinat, el genèric enlloc del pae (admeto que no sé quina diferència hi ha en això) i en apuntar aun repositori concret on hi ha uns drivers per aquesta gràfica i aquest kernel.

Vaig seguir les instruccions fil per randa menys el tema del 3D, que ja no el tenia activat, i quan vaig rebotar la màquina arrencava però no es veia res. 

Aquí vaig fer la sèrie d'operacions que explico dues rèpliques més amunt per treure el canvi al grub, i quan vaig aconseguir-ho la màquina va funcionar bé.

Per tant les operacions descrites al segon enllaç funcionen, menys el tema del canvi al grub, que allà ja diu que a vegades cal i a vegades no. Al meu cas no calia. 

Salut, i gràcies per la paciència

Lluís

---

