---
title: "Pèrdua de connexió amb wicd"
date: 2010-03-02
forum: Catalan Team
---

### Post by lo gambusí on 2010-03-02
Hola!

Escric este missatge per si algú pot donar-me un copet de mà.
:D
Resulta que vaig instal·lar lo wicd (gestor de xarxes) al meu ubuntu 9.10, i en instal·lar-se va desinstal·lar automàticament el programa gestor de connexions que hi havia anteriorment. 

Per alguna raó, però, lo wicd no detecta la connexió sense fils del meu pis (no en detecta cap, de fet) i això fa que em trobe en un atzucac: no puc connectar-me a internet perquè wicd no detecta lo *wifi*, i no puc (re)instal·lar l'antic gestor perquè no puc connectar-me a Internet.

Algú sap què podria fer?

Moles gràcies!!:p

---

### Post by mguerr35 on 2010-03-02
Hola,

si tens el cd o dvd pots afegir-lo com a repositori i ja podràs instal·lar algun gestor des d'aquí (network-manager per exemple).

Al posar el disc al lector ja t'ho detecta i treu un missatge per si el vols afegir.


Mario

---

### Post by oriolsbd on 2010-03-02
Des d'un altre ordinador on sí tinguis connexió, baixa't els paquets "network-manager" i "network-manager-gnome". Pots trobar els .deb al final d'aquests enllaços:
[http://packages.ubuntu.com/karmic/net/network-manager](http://packages.ubuntu.com/karmic/net/network-manager)
[http://packages.ubuntu.com/karmic/net/network-manager-gnome](http://packages.ubuntu.com/karmic/net/network-manager-gnome)

Un cop descarregats, amb un llapis USB els passes a qualsevol directori de l'ordinador on no tens connexió i els instal·les per mitjà de la comanda:
```
sudo dpkg -i network-*.deb
```

És possible que abans hagis de desinstal·lar el Wicd.

Salut!

---

### Post by lo gambusí on 2010-03-02
Perfecte, he fet lo que m'ha dit oriolbsd i ja torno a tenir lo network manager. Moltes gràcies!

---

