---
title: "No funciona el botó dret del ratolí"
date: 2010-10-25
forum: Catalan Team
---

### Post by LiLith Aleera on 2010-10-25
Hola,

Avui vaig instal·lar l'última de Ubuntu per Netbook, i tinc diverses fallades. Una d'elles és que el botó dret no em funciona, és com si no estigués activat, només fa la seva funció en la llançadora de l'esquerra, però en res més. És la primera vegada que uso Linux i no sé ben com configurar això o si és bug, perquè en aplicacions també m'he fixat que sota de tot les aplicacions queden com a ocultes i no es veuen, i el pitjor és que si instal·lo alguna cosa perdo una altra aplicació perquè va baixant.

Però bé, ara m'interessa això del botó dret, com podria activar-ho o el que sigui?

El meu Netbook és un Acer Aspire 1410 i la versió de Ubuntu l'última per Netbook, instal·lada des d'un USB.

Gràcies i una salutació,
[img]http://www.cheesebuerger.de/images/midi/liebe/a062.gif[/img]

---

### Post by kukat on 2010-10-26
Hola!!! 

Doncs per a configurar el ratolí pots anar a "Sistema" "Preferències", "Ratolí" i veure si tens alguna cosa mal configurada...però és una mica estrany. 
Tens els efectes d'escriptori habilitats???

Et recomane que et baixes la guia de l'Ubuntu 10.10 feta per un company del fòrum, Miquel Ubuntero:

[http://ubuntuforums.org/showthread.php?t=1597647](http://ubuntuforums.org/showthread.php?t=1597647)

Per cert, benvinguda al Fòrum vampiressa! ;)

---

### Post by LiLith Aleera on 2010-10-26
Doncs sí, la configuració del ratolí l'he mirat, però tampoc surt res referent al botó dret. 

No sé que vols dir amb "els efectes d'escriptori habilitats"...[img]http://www.cheesebuerger.de/images/midi/konfus/c066.gif[/img]

Ahir em vaig descarregar Ubuntu "normal", no el que és per Netbook, i estic pensant instal·lar-ho per veure si va millor. [img]http://smileys.sur-la-toile.com/repository/Reflexion/idee-puis-non.gif[/img]

Gràcies per la guia [img]http://www.cheesebuerger.de/images/midi/liebe/a062.gif[/img] i gràcies per la benvinguda.[img]http://www.cheesebuerger.de/images/midi/nahrung/a055.gif[/img]

---

### Post by wgarcia on 2010-10-26
Em sembla que de moment no hi ha funcionalitat per al botó dret del ratolí sobre l'escriptori que fa servir Unity (l'escriptori que s'instal·la a la edició Netbook d'Ubuntu, que es diu "mutter"). Per tant no és estrany que si cliques el botó dret sobre l'escriptori no faci res.

En quant al llançador d'aplicacions mira el vídeo que surt en aquest enllaç a veure si et serveix pel tema de les aplicacions "ocultes":

[http://www.webupd8.org/2010/06/new-ubuntu-unity-launcher-video-and.html](http://www.webupd8.org/2010/06/new-ubuntu-unity-launcher-video-and.html)

---

### Post by LiLith Aleera on 2010-10-26
Però és que tampoc fa res si poses el ratolí sobre un accés directe, no funciona en res [img]http://www.cheesebuerger.de/images/midi/frech/a024.gif[/img] només en el llançador de l'esquerra.

Si poso el Ubuntu que no és per Netbook m'anirà bé?

Li faré una ullada al vídeo també, gràcies.[img]http://www.cheesebuerger.de/images/midi/froehlich/a040.gif[/img]

Ara veient el vídeo, en la barra d'eines, tampoc em surt a mi això de sistema, aplicacions, etc...està sense res. Jo crec que no se'm va instal·lar bé, li falten coses.

---

### Post by kukat on 2010-10-26
no sabia això de la versió per a Netbooks del botó dret.....bo saber-ho! 

No entenc molt de versions per a Netbooks, però igual no necessites la versió normal... 

Tot i que sí no tens dades, tens temps, i acabes d'insta&#320;lar l'Ubuntu per primera vegada i no et convenç la versió per a Netbooks, no fa res provar...
;)

---

### Post by LiLith Aleera on 2010-10-26
Sí, em sembla que instal·laré Ubuntu novament però la versió que no és per Netbook. Si veig que no va bé, ja veuré que faig.

[img]http://www.cheesebuerger.de/images/midi/liebe/a062.gif[/img]

---

### Post by SiscoGarcia on 2010-10-27
Jo estic fent servir l'Unity en un netbook i la veritat és que no va gaire fi encara; hi ha detallets emprenyadors. De tota manera no et cal instal·lar l'escriptori gnome (l'habitual) ja que va inclòs amb l'Ubuntu Netbook Edition (Unity); només cal que a l'hora d'arrencar l'ubuntu, quan triïs amb quin usuari vols entrar, a la barra inferior on hi diu «Ubuntu Netbook Edition» despleguis el menú i triïs la versió d'escriptori (no recordo ben bé com ho diu) i podràs fer servir el gnome «normal».

Ara mateix no sé dir-te si quedarà predefinit per sessions successives o què, però amb dos clics ja tindràs l'escriptori més usable (encara que no està optimitzat per netbooks).

---

### Post by LiLith Aleera on 2010-10-28
Això no ho sabia...

Ahir vaig instal·lar la versió "normal" de Ubuntu i la veritat és que em va molt bé, no va lent ni res, m'agrada més. Encara que reconec que la llançadora aquesta de Unity anava molt bé, i crec que en el Ubuntu no es pot posar pel que he llegit. [img]http://www.cheesebuerger.de/images/midi/konfus/a014.gif[/img]

---

### Post by jalabop on 2010-10-31
Bon dia a tots i totes.

Fa pocs dies vaig fer el salt a la 10.10 edició Desktop de 64 bit (en principi volia mantenir la 10.04 LTS però no m'hi vaig poder estar) i he patit el mateix problema: el botó dret del touchpad del meu portàtil HP Pavilion Dv6 no funcionava. Sembla ser un problema entre el  kernel actual i el paquet xserver-xorg-input-synaptics (ho he d'investigar encara per saber exactament què ha passat).

He trobat dues sol·lucions buscant per internet:

- El primer que heu de fer és assegurar-vos que el vostre touchpad és de synpatics:

```
dmesg | grep -i synaptics
```- Una ràpida però que no m'agradava gaire com deixava el touchpad (no funcionava realment com un touchpad sinó com un mouse):

Obriu un terminal (Aplicacions --> accessoris --> terminal o bé feu alt+F2 i escriviu gnome-terminal) i copieu el següent codi (cada línia cal un intro):

```
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot

```- La sol·lució que ha fet que em funcioni (tot i que no del tot satisfactòriament) el touchpad correctament (és més complexa). Obrirem un terminal com en el cas anterior.

- Primer mirarem si tenim instal·lat el paquet dkms
```
dpkg --list | grep dkms
```
- Si no hi ha cap resultat i cal instal·lar-lo farem:
```
sudo apt-get install dkms
```- Ens haurem de baixar el següent pedaç. Haureu d'obrir el terminal al directori en el que el descarregueu.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/+attachment/1675262/+files/psmouse-2.6.35-22-generic-patched.tar.bz2](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/+attachment/1675262/+files/psmouse-2.6.35-22-generic-patched.tar.bz2)

-Obriu un terminal i dirigir-vos al directori on és troba el pedaç descarregat. Ara haureu de desempaquetar-lo i copiar-lo a /usr/src

```
tar -xjf psmouse-2.6.35-22-generic-patched.tar.bz2
 sudo cp -r psmouse-2.6.35-22-generic /usr/src/
 
```- En el mateix terminal s'han d'executar les següents comandes:
```
sudo dkms add -m psmouse -v 2.6.35-22-generic
sudo dkms build -m psmouse -v 2.6.35-22-generic
sudo dkms install -m psmouse -v 2.6.35-22-generic
```- En aquest punt toca reiniciar l'ordinador.

- Un cop reiniciat podem comprovar si s'ha carregat el nou mòdul:
```
sudo dkms status -m psmouse -v 2.6.35-22-generic
```- Si no us funciona o voleu desinstal·lar aquest nou mòdul heu de fer un terminal:
```
sudo dkms uninstall -m psmouse -v 2.6.35-22-generic
sudo dkms remove -m psmouse -v 2.6.35-22-generic --all
```En el meu cas han funcionat les dues opcions però cap de les dues em convenç la veritat. La primera fa que el comportament del touchpad sigui com el d'un mouse PS/2 estàndard i la segona, tot i fer funcionar l'scroll i el botó dret, té una sensibilitat impossible per treballar (quan vols copiar alguna frase, per exemple, és impossible ja que el punter marxa tot boig per la pantalla). Us recomano provar la primera opció ja que és més estable. Jo, tot i haver-lo configurat, segueixo amb el touchpad deshabilitat.

Esperarem a veure si ho sol·lucionen d'una vegada.

Font: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/94](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/94)

---

### Post by LiLith Aleera on 2010-11-01
Està bé com a solució temporal, la veritat és que no entenc com una cosa important com el botó dret no ho hagin tingut en compte...suposo que ho solucionaran en properes versions. [img]http://www.cheesebuerger.de/images/midi/nahrung/a040.gif[/img]

---

### Post by jalabop on 2010-11-02
Esperem que ho sol·lucionin ben aviat perquè és molt i molt molest treballar sense botó dret (de fet és quasi inviable) o amb un touchpad que no et permet subratllar una paraula sense tornar-se (i tornar-te) mig boig. 

De moment el tinc deshabilitat i treballo amb un mouse de tota la vida...

---

### Post by LiLith Aleera on 2010-11-02
Però és que amb el mouse de tota la vida tampoc funciona el botó dret. [img]http://www.cheesebuerger.de/images/midi/traurig/a010.gif[/img]

---

### Post by kimet on 2010-11-02
Reviseu la documentació de gnome sobre com configurar el ratolí, fa molt que no utilitzo gnome, però em sembla que hauria de funcionar.
[http://library.gnome.org/users/gnome-access-guide/stable/dtconfig-1.html.es](http://library.gnome.org/users/gnome-access-guide/stable/dtconfig-1.html.es)

Salut.

---

