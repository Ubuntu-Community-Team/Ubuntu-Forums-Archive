---
title: "Problemes amb les instal·lacions ubuntu 16.04"
date: 2016-05-02
forum: Catalan Team
---

### Post by bratac on 2016-05-02
Bones,

m'acabo d'instal·lar des de 0 ubuntu gnome 16.04. Tot correcte excepte pel fet que no em puc instal·lar alguns programes com el chromium el gimp o el gtranslate. Sempre em dóna un error de «dependencies» i d'aquí no en surto. Algú em pot donar un cop de mà?

Exemple:
> 
 gtranslator : Depèn: libgda-5.0-4 (>= 5.0.2) però no serà insta&#320;lat
               Depèn: libgdict-1.0-9 (>= 3.18.0) però no serà insta&#320;lat
               Depèn: libgdl-3-5 (>= 3.8.1) però no serà insta&#320;lat
               Depèn: gir1.2-gucharmap-2.90 però no serà insta&#320;lat
               Depèn: libpeas-1.0-0-python2loader però no serà insta&#320;lat
E: Dependències insatisfetes. Proveu amb «apt-get -f install» sense paquets (o especifiqueu una solució).

o 

> Els següents paquets tenen dependències sense satisfer:
 chromium-browser-l10n : Depèn: chromium-browser (>= 49.0.2623.108-0ubuntu1.1233) però no serà insta&#320;lat
                         Depèn: chromium-browser (< 49.0.2623.108-0ubuntu1.1233.1~) però no serà insta&#320;lat

o 
> 
 gimp : Depèn: libgimp2.0 (>= 2.8.16) però no serà insta&#320;lat
        Depèn: libgimp2.0 (<= 2.8.16-z) però no serà insta&#320;lat
        Depèn: gimp-data (>= 2.8.16) però no serà insta&#320;lat
        Depèn: gimp-data (<= 2.8.16-z) però no serà insta&#320;lat
        Depèn: python-gtk2 (>= 2.8.0) però no serà insta&#320;lat
E: Dependències insatisfetes. Proveu amb «apt-get -f install» sense paquets (o especifiqueu una solució).






Gràcies,

---

### Post by wgarcia on 2016-05-02
Has provat això que et suggereix, oi? És a dir, obrir una terminal, i entrar:
```
sudo apt-get -f install
```

---

### Post by bratac on 2016-05-02
Hola.

Gràcies per la resposta. Després de fer tot el procés em dóna el següent error:

> E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wgarcia on 2016-05-02
Sols diu això? 

A vegades queda un fitxer de bloqueig (perquè no hi hagi dos programes actualitzant a l'hora), que es pot eliminar amb:

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by bratac on 2016-05-03
Bones, 

ja he fet el > sudo rm /var/lib/dpkg/lock

I si faig el sudo apt-get -f install (un cop fet l'anterior) em dóna el mateix problema. Us pass

> sudo apt-get -f install
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
S'estan corregint les dependències&#8230; Fet
The following additional packages will be installed:
  chromium-browser
Paquets suggerits:
  webaccounts-chromium-extension unity-chromium-extension adobe-flashplugin
S'insta&#320;laran els paquets NOUS següents:
  chromium-browser
0 actualitzats, 1 nous a insta&#320;lar, 0 a suprimir i 2 no actualitzats.
1 no insta&#320;lats o suprimits completament.
S'ha d'obtenir 0 B/67,5 MB d'arxius.
Després d'aquesta operació s'empraran 265 MB d'espai en disc addicional.
Voleu continuar? [S/n] s
(S'està llegint la base de dades&#8230; hi ha 159727 fitxers i directoris instal·lats actualment.)
S'està preparant per a desempaquetar &#8230;/chromium-browser_49.0.2623.108-0ubuntu1.1233_amd64.deb&#8230;
S'està desempaquetant chromium-browser (49.0.2623.108-0ubuntu1.1233)&#8230;
dpkg-deb (subprocés): descomprimint l'element de l'arxiu: s'ha produït un error en lzma: les dades comprimides estan corrompudes
dpkg-deb: s'ha produït un error: el subprocés <descompressió> retornà el codi d'eixida d'error 2
dpkg: s'ha produït un error en processar l'arxiu /var/cache/apt/archives/chromium-browser_49.0.2623.108-0ubuntu1.1233_amd64.deb (--unpack):
 no es poden copiar les dades extretes de «./usr/lib/chromium-browser/libs/libwebcore_shared.so» a «/usr/lib/chromium-browser/libs/libwebcore_shared.so.dpkg-new»: s'ha trobat una fi de fitxer o flux inesperada
S'estan processant els activadors per a man-db (2.7.5-1)&#8230;
S'estan processant els activadors per a gnome-menus (3.13.3-6ubuntu3)&#8230;
S'estan processant els activadors per a desktop-file-utils (0.22-1ubuntu5)&#8230;
S'estan processant els activadors per a mime-support (3.59ubuntu1)&#8230;
S'estan processant els activadors per a hicolor-icon-theme (0.15-0ubuntu1)&#8230;
S'han trobat errors en processar:
 /var/cache/apt/archives/chromium-browser_49.0.2623.108-0ubuntu1.1233_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Gràcies!

---

### Post by bratac on 2016-05-03
Resolt:

> sudo apt-get purge chromium-browser*

> Sudo apt-get update

---

### Post by wgarcia on 2016-05-03
Perfecte! Penso que 
```
sudo apt-get dist-upgrade
```
potser també ho hauria pogut arreglar.

En tot cas seria útil si poses "Solved" al fil, perquè quedi de referència. Si obres el teu primer missatge al fil, a les pestanyes de dalt veuràs que hi ha una opció per marcar el fil com a "Solved".

---

