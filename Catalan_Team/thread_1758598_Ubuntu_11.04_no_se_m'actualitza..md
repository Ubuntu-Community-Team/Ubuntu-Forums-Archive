---
title: "Ubuntu 11.04 no se m'actualitza."
date: 2011-05-14
forum: Catalan Team
---

### Post by Arteazul on 2011-05-14
Hola a tothom,

Ja feia uns dies que pensava que l'Ubuntu no se m'actualitzava automàticament i vaig anar a l'actualitzador de gnome per a actualitzar manualment, i hem dona aquest missatge:

No es pot inicialitzar la informació dels paquets

S'ha produït un error irresoluble mentre s'inicialitzava la informació de paquets.

Informeu d'aquest error de l'update-manager i incloeu el missatge següent:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages, E:No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.'

Ho vaig intentar també amb la consola i hem dona el mateix missatge.

Pot algú ajudar-me? Moltes gràcies.

---

### Post by wgarcia on 2011-05-15
Mira el següent, sembla exactament el teu problema i la seva solució:

[http://ubuntuforums.org/showpost.php?p=10475669&postcount=6](http://ubuntuforums.org/showpost.php?p=10475669&postcount=6)

---

### Post by josep-maria on 2011-05-17
Em passa exactament igual. He fet això que diu de:

sudo rm /var/lib/apt/lists/* -vf

i em contesta:

rm: no s’ha pogut eliminar «/var/lib/apt/lists/partial»: És un directori

I ara què faig?

---

### Post by wgarcia on 2011-05-17
Doncs mira si així funciona (esborra el directori del que es queixa, i després els torna a crear):

sudo rm /var/lib/apt/lists/* -vfr

sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial

Seguit d'una sèrie de comandes que intenten acabar d'actualitzar tots els paquets que estiguin incomplets:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by josep-maria on 2011-06-03
Ja va bé. He fet tot això de sudo rm, mkdir, apt, etc. i ara va tot bé. Moltes gràcies.

---

