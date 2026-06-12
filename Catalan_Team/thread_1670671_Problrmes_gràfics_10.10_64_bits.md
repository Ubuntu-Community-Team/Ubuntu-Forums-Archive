---
title: "Problrmes gràfics 10.10 64 bits"
date: 2011-01-19
forum: Catalan Team
---

### Post by Mitsurugi on 2011-01-19
Hola a tothom, arran de la actualització que he fet avui al matí 19 de gener, des de que m'ha demanat reiniciar que al entrar, no es veu bé, es veuen com a interferencies, només es veu bé el fons de pantalla.

targeta ati radeon hd 4550 i ubuntu 10.10 64 bits, encara em falta cercar mes solucions i gent que hagi tingut problemes, de moment ho fico ací per si algu ha tingut  el mateix problema a veure que s'hi pot fer

---

### Post by wgarcia on 2011-01-19
El primer que pots provar és fer

sudo dpkg-reconfigure xserver-xorg

des d'una terminal, i tornar a iniciar a veure si ha millorat.

---

### Post by Mitsurugi on 2011-01-19
hi ha alguna manera d'iniciar el terminal abans que s'executi la gràfica? ho dic per que ho tinc dificil sino intuir la terminal ....

aki la millor imatge que he pogut fer del que es veu 

[http://img121.imageshack.us/img121/6366/20110119141805.jpg]("http://img121.imageshack.us/img121/6366/20110119141805.jpg")

---

### Post by wgarcia on 2011-01-19
Pots entrar en mode recuperació i escollir una de les opcions que t'ofereix per entrar amb gràfica simplificada o directament a una consola de superusuari.

---

### Post by Mitsurugi on 2011-01-19
.

---

### Post by Mitsurugi on 2011-01-19
.

---

### Post by Mitsurugi on 2011-01-19
.

---

### Post by Mitsurugi on 2011-01-19
.

---

### Post by Mitsurugi on 2011-01-19
.

---

### Post by Mitsurugi on 2011-01-19
Bé acabo d'entrar normal, obro terminal amb ctrl + alt + f1 i surt un bucle infinit amb aquest missatge

[drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

Sembla ser que l'error bé del linux headers bla bla bla -25

Enllaç del bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703352]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703352")

He hagut de tornar en el grup a un kernel "antic" 'Ubuntu, with Linux 2.6.35-24-generic'

Ara la meva pregunta és, com puc "desinstalar" el 'Linux 2.6.35-25-generic' que es el que em dona problemes, i que se m'inici sempre amb el que estic ara, o sigui el Linux 2.6.35-24-generic

Al canal m'han comentat que a l'arxiu /boot/grub/grub.cfg

Alla veig que hi ha uns "menuentry { }" haig de treure els corresponents o que?

---

### Post by kimet on 2011-01-19
No, a /etc/default/grub canvies la entrada:
GRUB_DEFAULT=0 per GRUB_DEFAULT=1  o per la que vulguis que arrenqui per defecte. Després executes update-grub com a root.


Salut.

---

### Post by kimet on 2011-01-19
No, a /etc/default/grub canvies GRUB_DEFAULT=0 per el número que correspongui a la entrada del kernel que vulguis que s'inicii per defecte, (començant per 0).
 
Salut


PD. que malament va la página no??

---

### Post by Mitsurugi on 2011-01-20
Però com se exactament quin numero te el antic linux headers?

No hi ha una manera de desinstalar el ........-25?

Per cert, el bug "original" és [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703553](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703553)

l'altre era un duplicat

---

### Post by wgarcia on 2011-01-20
Clica el menú Sistema -> Administració -> Gestor de paquets synaptic

Busca linux i marca linux-generic

Clica "Paquet" als menús de Synaptic

Clica "Força versió" i t'hauria de sortir la versió anterior que pots escollir.

Compte perquè no sé si aplica bé les dependències o has de mirar "a mà" de forçar també les versions de les dependències. 

Per frenar les actualitzacions fins que vegis que s'hagi corregit el problema:

sudo "echo <package> hold" | dpkg --set-selections


Quan vulguis treure el "hold":

sudo "echo <package> install" | dpkg --set-selections

---

### Post by kimet on 2011-01-20
> **Mitsurugi said:**
> Però com se exactament quin numero te el antic linux headers?

No hi ha una manera de desinstalar el ........-25?

Per cert, el bug "original" és [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703553](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703553)

l'altre era un duplicat


Els headers han d'anar amb la versió del nucli corresponent.(no podrás compilar els mòduls sense els headers).
 
La solució que jo em pensaba que volies, era arrencar amb el nucli anterior 2.6.35.24 per defecte, així donç el numero del grub_default que et deia correspón a la línia en que figura la entrada que vols que arrenqui per defecte començant desde cero.

---

### Post by Mitsurugi on 2011-01-21
Moltes gràcies companys, vaig a fer això que m'ha dit en @wgarcia

Sí @kimet, de fet volia saber-ho també, per comoditat de no anar fent ESC al iniciar cada cop, i seleccionar l'antic, però prefereixo no tocar el grup, no sigui que no arranqui res, que amb la bona sort que he tingut aquesta setmana ...

Gràcies de nou

---

