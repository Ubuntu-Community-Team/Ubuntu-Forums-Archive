---
title: "HDMI no emet só a la pantalla de la tele"
date: 2013-01-24
forum: Catalan Team
---

### Post by akyra on 2013-01-24
Hola,
Ahir vaig probar de veure en streaming una peli i pasar-la a la tele a través de HDMI i em va soptar que el video perfecte, però el só no arribava a la tele, i ho vaig haver de sentir a través de l'ordinador.

Utilitzu Ubuntu 12.04 64 bits i el kernel és el 3.2.0-36-generic.

Algú té idea de que pot ser?

Gracies

---

### Post by alpc360 on 2013-01-25
Pot ser que la sortida d'àudio no sigui la de HDMI tindràs que canviar-la.

Mira aquesta pàgina per que el situïs.

[http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/](http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/)

;)

---

### Post by akyra on 2013-01-27
Hola alpc360,

El problema es que no m'apareix la sortida d'audio HDMI en el menú de "Configuració de só", només m'apareixen els "Altaveus" i la "Sortida digital s/pdif)". No m'apareix la sortida ni conectant la HDMI ni abans de conectar-la.

En un altre ordinador que tinc quan connecto la sortida HDMI m'apareix en el menú de só la sortida HDMI que només haig de seleccionarla, pero en aquest ordinador simplement no surt.

He afegit en el grup2 l'opció de  "radeon.audio=1" com indicava en la web que m'has pasat, però no he notat canvis.
La meva tarja de video és una ATI Mobility Radeon&#8482; HD 4570, per això he aplicat aquest canvi.

Per cert, després de fer el:
sudo gedit /boot/grub/grub.cfg

i afegir la linea radeon.audio=1 al final del fitxer, he fet un 
sudo update-grub

i he reiniciat, però desp&#341;es he tornat a mirar si existia la linea, i s'ha esborrat.

No tinc posats el drivers propietaris de ATI, era una mica reticent a fer-ho, però potser és la posibilitat.


Alguna idea més?

---

### Post by akyra on 2013-01-27
Bé, després d'investigar una mica més he trobat la solució que m'ha portat a la solució, que és el mateix que el que em deia a la pagina que m'han indicat, però millor explicat i no m'ha calgut instal·lar els drivers propietaris.

La pàgina en qüestió es aquesta:
[http://lucasromerodb.blogspot.com.es/2012/04/sin-salida-de-sonido-hdmi-en-ubuntu-ati.html]("http://lucasromerodb.blogspot.com.es/2012/04/sin-salida-de-sonido-hdmi-en-ubuntu-ati.html")

I resumint, la solució és fer el següent:
1.- Obrim el terminal i edit el fitxer del grub:

    sudo gedit /etc/default/grub

2 - Després que obrim l'arxiu busquem el texte:

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

i el substituim per:

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

3.- Guardem l'arxiu i el tanquem.

4 - Actualitzem el GRUB:

    sudo update-grub

5.- Reiniciem l'ordinador.

Bé això és tot i a mi m'ha funcionat.

Espero que ajudi a algú.

Salutacions

---

### Post by alpc360 on 2013-01-28
M'alegro que ho hagis pogut solucionar.

Sobre el /etc/grub/grub.cfg cada vegada que facis update-grub2 es matxacara el fitxer ja que el torna a generar, per això tens que configurar-ho  en /etc/default/grub.

Recordo si a la gent que en el fitxer grub.conf posa en la primera línia "NO EDIT THIS FILE"
):P):P):P):P

---

### Post by akyra on 2013-01-29
En les vesions anteriors d'Ubuntu diria que si que podies editar aquest fitxer, però suposo que al canviar al grub2 això també ha canviat.

També vaig descobrir l'aplicacio "boot-repair" que serveix per editar i si cal reparar el grub, en ella vaig veure que obria un altre fitxer.

Bé, ara obriré un altra fil en el tinc un altre ordinador que el no em funciona bé és la imatge en la sortida de HDMI. però sí el só.

Gracies

---

### Post by U-Joan on 2013-02-11
Uoooo per fi he pogut solucionar aquest tema... Em passava el mateix. Moltes gràcies Akyra!

---

### Post by akyra on 2013-02-12
De res, que una solució vagi bé als demés anima a continuar-ne fent.

Salutacions

---

