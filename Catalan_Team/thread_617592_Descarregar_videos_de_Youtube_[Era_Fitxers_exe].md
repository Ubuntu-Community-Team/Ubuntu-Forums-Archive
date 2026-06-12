---
title: "Descarregar videos de Youtube [Era: Fitxers exe]"
date: 2007-11-19
forum: Catalan Team
---

### Post by lluisanunez on 2007-11-19
Vols el youtube downloader per a guardar videos de Youtube al teu disc? Si és així, hi ha serveis web que t'ho fan, per exemple:
[http://vconvert.net/](http://vconvert.net/)

---

### Post by oriolsbd on 2007-11-19
Si fas servir el Firefox, també hi ha diverses extensions que et permet baixar-te'ls (els de YouTube i els d'altres webs de vídeos). Jo faig servir el VideoDownloader:
[http://javimoya.com/blog/youtube_en.php](http://javimoya.com/blog/youtube_en.php)

Però si busques download Video a [https://addons.mozilla.org](https://addons.mozilla.org), n'hi ha uns quants més.

Salut!

---

### Post by CarlesOriol on 2007-11-19
El miro està als repositoris i es molt interessant... però aquest fil età canviant el tema del titol no?

---

### Post by jerec on 2007-11-19
Ja ho vaig adelantar a la meva resposta.:)

---

### Post by RainCT on 2007-11-19
Jo he fet un programa per a això, el [QtTube](https://wiki.ubuntu.com/QtTube). Per a insta&#320;lar-lo executa la següent línia en una terminal (no t'espantis que ho he provat ;P):

```

sudo aptitude -y install python-qt4 youtube-dl && wget https://edge.launchpad.net/qttube/0.x/0.2/+download/QtTube-0.2~pre1.tar.gz --no-check-certificate && gunzip ./QtTube-0.2~pre1.tar.gz && tar -xvvf QtTube-0.2~pre1.tar && rm ./QtTube-0.2~pre1.tar && cd ./qttube-0.2~pre1 && sudo ./install "/usr/local"

```

I aquesta:

```

sudo cp ./data/qttube.desktop /usr/share/applications && sudo cp ./data/qttube-48x48.png /usr/share/pixmaps/qttube.png && sudo ln /usr/local/QtTube/qttube /usr/local/bin/qttube && cd .. && rm ./qttube-0.2~pre1 -r

```

Espero que d'aquí poc acabaré una nova versió (que podrà convertir els vídeos a un altre format, com OGG o AVI, perquè es puguin reproduir millor) i d'aquesta en faré un paquet .deb.

Salut

---

### Post by lluisanunez on 2007-11-19
> **RainCT said:**
> 
Espero que d'aquí poc acabaré una nova versió (que podrà convertir els vídeos a un altre format, com OGG o AVI, perquè es puguin reproduir millor) i d'aquesta en faré un paquet .deb.


Interessant, **RainCT**, ara a quins formats converteix?

**CarlesOriol**, sabem que tens superpoders, si parteixes aquest thread en Papapep no ens renyarà :)

---

### Post by RainCT on 2007-11-19
> **lluisanunez said:**
> Interessant, **RainCT**, ara a quins formats converteix?

Ara mateix no els converteix a cap, simplement baixa l'arxiu flv (flash).

---

### Post by papapep on 2007-11-19
Us fotaré a tots a gal·leres, colla de insubmisos... :-D

---

### Post by Druiling on 2007-11-20
Hola tothom.
Bé. Finalment, m'he baixat un complement de Firefox que descarrega al disc i va prou bé.
YouPlayer. 
Per si a algú li interessa, aquí deixo el link.
[https://addons.mozilla.org/es-ES/firefox/browse/type:1/cat:38]("https://addons.mozilla.org/es-ES/firefox/browse/type:1/cat:38")
Gràcies.
D.

---

