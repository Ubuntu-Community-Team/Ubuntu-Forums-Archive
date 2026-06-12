---
title: "Pantalla conectada a portàtil no funciona."
date: 2011-12-28
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2011-12-28
Bones.
Tinc un portàtil Latitude E6400 amb una pantalla conectada a la sortida vga.
Hi tinc un Xubuntu 10.04 insta&#320;lat que, en prèmer les tecles Func+F8, puc fer ús de la pantalla conectada. Va perfecte.

Ara hi he insta&#320;lat Ubuntu 11.10 amb la sorpresa que el "Func.+F8" no em ruttle i no puc fer ús de la pantalla externa :(

No tinc clar si té res a veure amb Unity (que és el que sospito).
Algú pot ajudar-me?
Gràcies.

---

### Post by CarlesOriol on 2011-12-28
El unity no té res a veure amb la gestió del monitor no és gestor de la composició de video ni de finestres.

Has provat de configurar la pantalla externa amb la utilitat "Pantalles"?
Has provat el unity2d que usa el metacity (em sembla) en comptes del compiz?
Has provat el gnome-shell que duu un gestor propi?

---

### Post by Miquel Ubuntero on 2011-12-28
He provat de configurar la pantalla externa amb la utilitat "Pantalles" i he aconseguit veure les dues pantalles a l'hora. Però no he pogut apagar la del portàtil mentre faig ús de l'externa. A més, en reiniciar el PC, a deixat de funcionar. Estic intentant d'esbrinar què passa?

Abans de provar l'esmentat al paràgraf anterior, he provat provat el unity2d sense cap éxit.

Això del gnome-shell no ho he provat i no tinc clar què és. Mira que sóc "novato". Bé, ho he llegit una mica al wikipèdia. Si ho he entès bé, primer l'hauré d'insta&#320;lar, oi que si? Perquè crec que no el tinc ???

---

### Post by wgarcia on 2011-12-28
Quina targeta gràfica tens? Potser a l'actualització no s'ha instal·lat el controlador propietari que et permetia fer la exportació de pantalla que descrius de versions anteriors.

---

### Post by Miquel Ubuntero on 2011-12-28
No recordo quina tarja té aquest portàtil. A informació del sistema hi diu tarja desconeguda.

---

### Post by wgarcia on 2011-12-28
Fent des d'una terminal

```
lspci | grep -i vga
```

et diu tarja desconeguda?

---

### Post by Miquel Ubuntero on 2011-12-29
Tarja:
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Per cert, he provat el gnome-shell. Al intentar fer ús de la pantalla externa, fa una cosa bastant "divertida": Veig part de l'escriptori en una pantalla i part en l'altra. Com si tingues una pantalla doble gran partida en dos. Pot ser pràctic però no és el que jo vull. 

Ah! i gràcies per la vostra ajuda ;)

---

### Post by wgarcia on 2011-12-29
Doncs amb aquesta targeta Intel no necessites controladors propietaris. No entenc exactament el que vols fer, però segons em sembla entendre, vols simplement projectar la teva pantalla a un monitor extern, és a dir com quan projectem la pantalla a un projector, oi? En aquest cas em sembla que el que has de fer és iniciar l'ordinador amb la pantalla externa connectada, fer ús d'alguna combinació de tecles amb la tecla "fn" (funció, això varia de model en model), i acabar de configurar la resolució de pantalla o altres coses un cop que estigui connectada la pantalla externa.

---

### Post by Miquel Ubuntero on 2011-12-29
Sí, correcte, el que voldria és projectar la pantalla al monitor extern.
Ja inicio el PC amb la pantalla connectada i engegada, però res.

El que sem fa estrany és, que amb Xubuntu i altres sistemes com Linux MInt, si que ho puc fer: amb les tecles Fn+F8, però amb Ubuntu 11.10 no hi ha manera. 

Bé, de fet no és greu per a mi. Continuo utilitzant Xubuntu que ja m'està bé. Lo del ús de la 11.10 ho volia per fer proves. Ja ho faré amb Virtual Box com he fet altres cops. La qüestió és que m'agrada utilitzar una pantalla de 19" amb el portàtil. Ja sabeu, amb l'edat, quan més gran la pantalla millor. :)

Moltes gràcies i que provi l'any nou! :popcorn:

---

### Post by kimet on 2011-12-29
No se si xrander està instal.lat a ubuntu. De totes maneres ho pots provar.

```
xrandr --current
```
Et dirà els monitors conectats

```
xrandr --output VGA1
```
Sortida al monitor amb el nom VGA1.

```
xrandr --output VGA1 --fb 1280x1024
```
Sortida amb nom VGA1 resolució 1280x1024

```
man xrandr
```
Per saber totes les opcions.

Salut.

---

### Post by wgarcia on 2011-12-29
El fet que no ho puguis fer amb Ubuntu pot tenir a veure amb el nucli actual d'Ubuntu. Quan et refereixes a Xubuntu, també estàs fent servir la versió 11.10?

---

### Post by Miquel Ubuntero on 2011-12-29
Hola de nou.
He estat provant xrandr, que si ve amb Ubuntu 11.10
He pogut veure que hi detecta una pantalla al vga1 i la puc configurar (la resolució). Però no la puc activar o desactivar a voluntat.

Fent varies proves, sense voler, un cop he iniciat el portàtil amb la pantalla externa apagada. La sorpresa ha estat que, en engegar-la, a funcionat. Continuo sense poder controlar-la a voluntat. De fet, si remeno l'opció Monitors de la configuració d'Ubuntu, s'apaga i no la puc fer encendre de nou.

Ara bé, si inicio amb monitor apagat, ja se que el puc engegar i fer-ne ús. Ja és un primer pas al menys per poder utilitzar-lo.

Gràcies a tots pel vostre interès.

---

### Post by kimet on 2011-12-29
Provant xrandr, em funciona bé amb intel:

amb:
```
xrandr --auto
```
S'em conecta els dos monitors
```
xrandr --output VGA1 --fb 1280x1024
```
El poso a la resolució que vull, i:
```
xrandr --output VGA1 --auto --right-of LVDS1
```
En veig un a continuació del altre.
I per apagar-ne un:
```
xrandr --output LVDS1 --off
```



Salut

---

### Post by Miquel Ubuntero on 2011-12-29
Hola Kimet.
Fent això últim que comentes, només he aconseguit el mateix que abans: Tindre l'escriptori repartit en dos pantalles. Un efecte curiós i potser útil per algú altre.

---

### Post by Miquel Ubuntero on 2011-12-30
Hola de nou.
Rectifico el que he dit abans.
Finalment, gràcies a la informació del Kimet, ho he aconseguit amb les següents ordres:

xrandr --output VGA1 --fb 1280x800
xrandr --output VGA1 --auto --right-of LVDS1
xrandr --output LVDS1 --off

D'aquesta manera si que tinc l'escriptori sencer a la pantalla externa, i la del portàtil apagada.

Llàstima que no funcionin les tecles Fn+F8 (tal com va amb Xubuntu), donat que és un pèl més senzill.

Però bé, gràcies, ja ho tenim!

---

### Post by kimet on 2011-12-30
No sé com es configura el bindatge de tecles a gnome, hi ha d'haver algún programa gràfic per a fer-ho. Si ho trobes només hi hauríes de posar les ordres que vols que s'executin al premer la combinació de tecles que trïis, P.Ex:
```
xrandr --output VGA1 --auto --fb 1280x800 --output LVDS1 --off
```

Una altre manera seria fer un script i posarlo en una icona a l'escriptori.
Obres un editor, hi escrius:
```
#!/bin/bash
xrandr --output VGA1 --auto --fb 1280x800 --output LVDS1 --off
```
Li poses el nom que vulguis, el guardes, li dones permisos d'execució i l'enllces a l'escriptori per tenir-lo mes accesible.

A més la resolució dels diferents monitors la podríes definir a l'archiu de configuració de xorg /etc/X11/xorg.conf, però potser sigui innecesari.

Bon any

---

