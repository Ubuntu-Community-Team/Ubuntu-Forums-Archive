---
title: "En iniciar, la pàgina es queda en lila"
date: 2012-03-22
forum: Catalan Team
---

### Post by Jayhawker on 2012-03-22
Hola, 

Tinc Linux Ubuntu 11/10 instal·lat mitjançant wubi en Windows. M'he vist obligat a fer un shut down perquè se m'havia quedat tot estancat. Llavors, quan he volgut entrar de nou, un cop he escollit Ubuntu, m'apareix la pantalla lila que, habitualment, després d'un segons, dóna pas a la finestreta de l'esquerra on posar-hi el password. Però ara, es queda estancat en la pantalla lila i no fa res més. 

Sabeu d'alguna manera de poder solucionar això sense haver de reinstal·lar l'11/10 i haver de tornar a carregar tot el que el sistema no porta incorporat, i que no és poc? A banda que perdria documents. 

Merci per la vostra atenció i ajut.

---

### Post by wgarcia on 2012-03-23
No sé molt bé com funciona Wubi, però una primera recomanació és que si fas un ús continuat d'Ubuntu et convindria fer una instal·lació pròpia al disc, al costat de l'altre sistema operatiu si et fa falta, perquè Wubi és més que res per provar l'Ubuntu, però es recomana fer una instal·lació completa en cas d'ús continuat. Per tant recomanaria que si recuperes les dades que tens a l'Ubuntu "Wubi", que consideris fer la instal·lació al disc.

Coses que pots provar per re-iniciar l'Ubuntu:

1) Tens un "recovery mode" en les opcions d'inici? Pots provar iniciar des d'aquí i veure si pots actualitzar algun paquet gràfic.

2) Prémer Control-Alt-F1 a veure si et dóna accés a una línia de comandes. Dins de la línia de comandes veure si pots actualitzar algun paquet gràfic.

Algunes instruccions a la línia de comandes que poden ser útils per recuperar la gràfica:

```
sudo service restart lightdm
```

Aquesta t'hauria de donar acccés a la pantalla d'inici o donar-te algun error.

Per veure si ha quedat alguna actualització sense completar, a la línia de comandes pots provar:

```
sudo dpkg --configure -a
sudo apt-get install -f 
```

O per veure si reconfigurant el servidor gràfic ho arregla:
```
sudo dpkg-reconfigure xserver-xorg
```

Però com deia crec que el més convenient és intentar fer una instal·lació una mica més permanent de l'Ubuntu, perquè l'Wubi no és més que un truc per fer-lo funcionar dins de Windows.

---

