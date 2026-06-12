---
title: "error d'instal.lació"
date: 2010-10-25
forum: Catalan Team
---

### Post by gilcent on 2010-10-25
Hola gent,

Des de fa dies que intento instal.lar nou programari i em surt sempre el mateix error;
S'ha produït un error en la instal·lació del paquet. S'està intentant restablir.
dpkg: s'ha produït un error d'anàlisi, al fitxer «/var/lib/dpkg/available» prop de la línia 30230 paquet «ubuntu-docs»: en aquest context no es permet un valor pel camp «config-version»


Sabeu com ho puc resoldre?

---

### Post by kukat on 2010-10-26
Quan tinc un error insta&#320;lant programari, el primer que faig és teclejar aquestes dues commandes a la terminal:

[B][I]dpkg --configure -a 
apt-get -f install[/I][/B]

S'encarreguen d'arreglar paquets trencats....


Per cert, benvingut a la web d'Ubuntu Catalan Team!!!

No oblides presentar-te al nostre [Fil de Benvinguda]("http://ubuntuforums.org/showthread.php?t=562776"), i de llegir-te [les normes del Fòrum]("http://ubuntuforums.org/showthread.php?t=599965")!!!

---

### Post by gilcent on 2010-10-26
Hola Kukat,

He fet el que em deies i em demana privilegis com a superusuari. Llavors he escrit;  ***sudo ***[B][I]dpkg --configure -a 
apt-get -f install
[/I][/B]llavors teclejo la contrasenya i novament em surt; dpkg s'ha produït un error d'anàlisi, al fitxer «/var/lib/dpkg/available» prop de la línia 30230 paquet «ubuntu-docs»:
en aquest context no es permet un valor pel camp «config-version»; 
m'oblido d'algun pas?

Merci

---

### Post by kukat on 2010-10-27
Fes primer ***sudo dpkg --configure -a*** 

i després ***sudo apt-get -f install***

Suposadament aquestes comandes arreglen els paquets trencats. 

Mira a vorer que et surt amb aquestes comandes

;)

---

### Post by gilcent on 2010-10-27
Hola Kukat,

He seguit els passos que m'has dit i em dóna el mateix error. Crec que m'esperaré a que surti una nova versió i l'actualitzaré, ja que encara tinc la 9.10 karmic koala. Vejam si així em funciona.

Merci per tot
Fins aviat

---

### Post by oriolsbd on 2010-10-28
Hola,

Això no és realment un error bloquejant (pots seguir instal·lant paquets, oi?), sinó més aviat un avís. Prova això:
Primer, fes-te còpia de seguretat del fitxer "available":
```
cd /var/lib/dpkg
sudo cp available available.antic
```
Ara, sense moure't del directori, edita el fitxer "available":
```
sudo gedit available
```
En aquest fitxer, cerca el paquet "ubuntu-docs" (la línia et dirà "Package: ubuntu-docs". Esborra des d'aquesta línia fins a la següent que comenci amb "Package: " (aquesta segona no inclosa). Desa els canvis i actualitza la informació dels repositoris:
```
sudo apt-get update
```
En principi, t'hauria de funcionar.

Salut!

---

### Post by gilcent on 2010-11-01
Hola Oriolsbd,

Ara sí que em funciona tot correctament. He seguit tots els passos que em deies i finalment he pogut fer les actualitzacions corresponents.

Merci
Fins aviat

---

### Post by wgarcia on 2010-11-01
Doncs faries un favor al fòrum si amb "Thread tools" esculls "Solved".

---

### Post by gilcent on 2010-11-11
Hola wgarcia,

Mil disculpes, vaig buscar el "solved" però no el vaig trobar.

---

### Post by wgarcia on 2010-11-12
Sembla que finalment sí que el vas trobar perquè ja es veu correctament.

---

