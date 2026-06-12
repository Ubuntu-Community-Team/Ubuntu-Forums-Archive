---
title: "labyrinth no obra"
date: 2010-02-01
forum: Catalan Team
---

### Post by abosch on 2010-02-01
bones,

faig servir el Labyrinth però des de vaig amb KK no l'havia obert. Fa com si anés a obrir-se però no. He [cercat i trobat]("https://bugs.launchpad.net/ubuntu/+source/labyrinth/+bug/86503") (em sembla) que han localitzat un bug, i donen solució. És això ...



[HTML]thefluxster  wrote on 2009-10-06:  	  #23

From launchpad Bug 327174:
"... At least in jaunty we're using python2.6, so changing line 40 to:
   sys.path.insert(0, abspath("/usr/lib/python2.6/dist-packages/labyrinth"))
and installing python-numeric should fix all problems. Its running here."

I can confirm this hack worked for me too.
Cristian V wrote on 2009-11-03: 	#24

I confirm that the thefluxter's solution above works perfectly in Ubuntu 9.10. Thanks!
[/HTML]


no sé com he de fer aquest canvi ... Algú ha solucionat el problema i/o em pot guiar ?

gràciees

:)

---

### Post by papapep on 2010-02-01
> no sé com he de fer aquest canvi

Doncs cal que editis el fitxer de nom "labyrinth", que suposo que deu ser a /usr/bin, però l'hauries de buscar, i canviar el que hi hagi a la línia 40 pel que et diu el post que has referenciat:

```
sys.path.insert(0, abspath("/usr/lib/python2.6/dist-packages/labyrinth"))
```

A més, et diu que instal·lis el paquet "python-numeric":

```
sudo aptitude install python-numeric
```

Segons això, jo ni tan sols sé què fa el labyrinth aquest, t'hauria de funcionar. Això sempre que facis servir el python2.6. Si fas servir el 2.5 ja no sé si et servirà la sol·lució aquesta.

Amb això veuràs quina versió tens instal·lada:

```
sudo aptitude search python2.|grep ^i
```

---

### Post by abosch on 2010-02-04
solucionat! moltes gràcies.

> què fa 

és un simple (senzill d'utilitzar) [programa]("http://www.gnome.org/~dscorgie/labyrinth.html") per fer diagrames, organitzar-se gràficament, vaja això dels mapes mentals ... suposo que n'hi ha que fan molt més i blablabla  , però no necessito més :D

Per terminal he editat el fitxer per la ruta que em deies a abans (amb el sudo gedit davant), he fet el canvi i avall. De totes maneres en fer-ho el canvi m'ha quedat un dubte de procediment: 
abans havia provat d'obrir directament amb tota la ruta complerta al fitxer de text o sigui```
sudo gedit usr/bin/labyrinth
``` i m'apareixia en blanc, com és? I relacionat amb també, hi ha alguna manera d'obrir en mode gràfic (o sigui sense terminal, un cop situat al directori usr/bin ) directament el fitxer de text amb permís per modificar-lo? 


gràcies

---

### Post by papapep on 2010-02-04
> abans havia provat d'obrir directament amb tota la ruta complerta al fitxer de text o sigui
Code:

sudo gedit usr/bin/labyrinth

i m'apareixia en blanc, com és?

Si ho provaves exactament com has posat ara, per que no li donaves el camí correcte. Et falta una barra / davant usr.

> hi ha alguna manera d'obrir en mode gràfic (o sigui sense terminal, un cop situat al directori usr/bin ) directament el fitxer de text amb permís per modificar-lo?

Fas Alt+F2, i poses dins la finestra que se t'obrirà:

```
gksudo gedit /elfitxer/que/vols/editar
```

ha de ser **gksudo**, i no sudo, ja que no fer-ho així pot portar problemes posteriors amb fitxers de configuració de l'entorn gràfic.

---

### Post by abosch on 2010-02-04
genial! moltes gràcies:D

---

