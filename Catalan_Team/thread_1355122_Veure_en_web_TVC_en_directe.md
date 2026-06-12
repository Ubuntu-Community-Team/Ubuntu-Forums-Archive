---
title: "Veure en web TVC en directe"
date: 2009-12-14
forum: Catalan Team
---

### Post by Curial on 2009-12-14
Com ho feu per veure en directe TVC per internet?

Sí que veig els programes enregistrats, no puc fer el mateix però amb la programació en directe.


Salut.

Edito: Amb Karmic Koala

---

### Post by kukat on 2009-12-15
Doncs jo estic veient-ho perfectament aquí: 
[http://www.tv3.cat/directes](http://www.tv3.cat/directes)

A pesar que hi ha programes que no es poden fer en directe a la xarxa per temes de copyright i coses d'aquetes.

---

### Post by anna_marti_gomez on 2009-12-15
> **kukat said:**
> Doncs jo estic veient-ho perfectament aquí: 
[http://www.tv3.cat/directes](http://www.tv3.cat/directes)



Kukat, tens instal·lat Ubuntu-restricted-extras? Crec que pot ser que el problema/solució vingui per aquí.

---

### Post by kukat on 2009-12-15
Si, tinc insta&#320;lats els Ubuntu Restricted Extras, i a banda tot açò:

    sudo wget [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list) --output-document=/etc/apt/sources.list.d/medibuntu.list; \
    sudo aptitude update && sudo aptitude -y --allow-untrusted install medibuntu-keyring && sudo aptitude update; \
    sudo add-apt-repository ppa:chromium-daily; \
    sudo aptitude update; \
    sudo aptitude -y install chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-nonfree chromium-codecs-ffmpeg; \
    sudo aptitude -y install ubuntu-restricted-extras \
    flashplugin-nonfree-extrasound libdvdcss2 libdvdread4 \
    w32codecs non-free-codecs k3b libk3b6-extracodecs kde-i18n-es \
    exaile banshee mplayer vlc smplayer \
    sun-java6-fonts sun-java6-jre sun-java6-plugin \
    rar p7zip-full unace unzip \
    compizconfig-settings-manager emerald fusion-icon \
    pidgin amsn emesene amule deluge vuze mozplugger \
    chromium-browser openshot; \
    sudo fc-cache

Que ho vaig extraure [**_d'aquest bloc_**]("http://moramorao.wordpress.com/2009/10/31/poner-apunto-ubuntu-karmic-koala/")

---

### Post by Tomàs M. on 2009-12-15
Prova-ho amb un perfil nou: firefox -profilemanager. Jo fa uns dies me'n vaig copiar un d'antic perquè amb el que feia servir normalment em passava el mateix, i avui veig que torna a fer el ruc. Encara no n'he tret l'entrellat. Ni desactivant l'adblock plus per a tv3.cat (que en els vídeos enregistrats sí que em donava problemes)...

Quina bestiesa... reiniciant el firefox es veu... Quan tingui temps miraré [http://tinyurl.com/ydraomh](http://tinyurl.com/ydraomh) i [http://tinyurl.com/yb3bsm6](http://tinyurl.com/yb3bsm6) a veure si aclareixo alguna cosa.

---

### Post by anna_marti_gomez on 2009-12-16
> **Curial said:**
> Com ho feu per veure en directe TVC per internet?

Sí que veig els programes enregistrats, no puc fer el mateix però amb la programació en directe.


Curial, prova d'instal·lar-te els ubuntu-restrected-extras. Crec que n'hauries de tenir prou:
```
 sudo apt-get install ubuntu-restrected-extras
```

Bon dia a tothom!

---

### Post by Curial on 2009-12-18
> **anna_marti_gomez said:**
> Curial, prova d'instal·lar-te els ubuntu-restrected-extras. Crec que n'hauries de tenir prou:
```
 sudo apt-get install ubuntu-restrected-extras
```

Bon dia a tothom!

Moltes gràcies Anna, amb això s'ha solucionat!!

Emperò és  sudo apt-get install ubuntu-restr[COLOR="Red"]**i**[/COLOR]cted-extras.

:-)

Gràcies a tots.
Bon Nadal.

---

### Post by anna_marti_gomez on 2009-12-18
> **Curial said:**
> 
Emperò és  sudo apt-get install ubuntu-restr[COLOR="Red"]**i**[/COLOR]cted-extras.

:-)

:!:

(és clar que sí!)

---

