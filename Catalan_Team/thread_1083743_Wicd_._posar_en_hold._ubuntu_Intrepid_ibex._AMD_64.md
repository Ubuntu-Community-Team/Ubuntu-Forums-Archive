---
title: "Wicd . posar en hold. ubuntu Intrepid ibex. AMD 64x2"
date: 2009-03-01
forum: Catalan Team
---

### Post by venusfenix on 2009-03-01
Buenas,

vull posar en hold algunes aplicacions, entre elles el wicd. seguin les indicacions de Papapep.
el tema es que no se el nom del paquet a posar en hold. 
com averiguar-lo???

Gracies,

---

### Post by papapep on 2009-03-02
Per exemple?

---

### Post by ggoscarl on 2009-03-02
Ara mateix acabo de llegir un article a mundogeek que en parla:

[http://mundogeek.net/archivos/2009/03/01/11-cosas-que-necesitas-saber-para-convertirte-en-un-experto-de-apt/](http://mundogeek.net/archivos/2009/03/01/11-cosas-que-necesitas-saber-para-convertirte-en-un-experto-de-apt/)


Per trobar a quin paquet pertany un arxiu:

dpkg -S archivomisterioso.cfg

---

### Post by venusfenix on 2009-03-02
ara per ara, vull posar el hold el wicd.
he probat amb :

sudo aptitude hold wicd
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
No s'instal·larà, actualitzarà o suprimirà cap paquet.
0 paquets a actualitzar, 0 a instal·lar, 0 a suprimir i 1 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
S'està escrivint la informació d'estat estesa... Fet
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet


entenc que es correcte pero el sinaptic continua dien que hi ha una actualitzacio del wicd.

Gracies,

---

### Post by venusfenix on 2009-03-02
he probat amb:

aptitude show wicd
Paquet: wicd
Nou: sí
Estat: instal·lat
Instal·lat automàticament: no
Versió: 1.5.5
Prioritat: extra
Secció: net
Mantenidor: Adam Blackburn <compwiz18@gmail.com>
Mida descomprimit: 1823k
Depèn: python, python-gtk2, python-dbus | python2.4-dbus, wpasupplicant,
        python-glade2, wireless-tools


i sembla correcte. llavors, que falla???

gracies,

---

### Post by papapep on 2009-03-02
No t'has llegit tot l'apunt que et vaig passar. Hi ha més opcions.

---

### Post by venusfenix on 2009-03-02
ostres, o sento, pero, l'he tornat a llegir, i no "pispo", t'ho juro.
he anat linea per linea, fent tot el que possaba, i funciona el post actualitzat pero no el de l'inici. he acabat tot el post, i llestos. 
pero el tema es el següent, esta clar que esta marcat per no actualitzar-se. la pregunta es perqué el gestors d'actualitzacions continua sortint??
malgrat que está selectionat, el comentari del propi gestor es "MIDA DE LA BAIXADA = 0KB"

entenc que es tot correcte???


perdó pel meu profanatisme, pero, aixo, encara soc profà en aquests temes.

Gracies,

---

### Post by papapep on 2009-03-02
Si quan fas un: 

```
sudo aptitude search wicd
```

Els primers dos caràcters de la resposta són

```
ih
```

ja et pots oblidar dels programes gràfics, ho tens ja com volies. :)

---

### Post by venusfenix on 2009-03-02
buenas,

llavors, ho havia fet be, OK!! gracies!!!

fins a la proxima!!

---

