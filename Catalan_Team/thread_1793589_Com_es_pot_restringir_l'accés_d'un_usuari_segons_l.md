---
title: "Com es pot restringir l'accés d'un usuari segons l'hora?"
date: 2011-06-29
forum: Catalan Team
---

### Post by lpargemi on 2011-06-29
Hola

Tinc una màquina amb Ubuntu 10.04, de 64 bits, i amb diversos usuaris. A més tinc fills desvagats per casa -coses de les vacances- que no vull que a totes hores estiguin a l'ordinador. Hi ha alguna manera d'autoritzar un usuari o un grup d'usuaris només en unes hores concretes? 

Salut

Lluís

---

### Post by oriolsbd on 2011-06-30
El Gnome Nanny ho pot fer:

[http://www.gnulinux.cat/2010/02/gnome-nanny-control-parental-gnome/](http://www.gnulinux.cat/2010/02/gnome-nanny-control-parental-gnome/)

Em sembla que no hi és als repositoris d'Ubuntu 10.04, o sigui que t'hauràs de configurar el seu PPA. Pots instal·lar-lo executant el següent:
```
sudo add-apt-repository ppa:nanny/ppa
sudo apt-get update
sudo apt-get install nanny
```

Salut!

---

### Post by lpargemi on 2011-07-01
> **oriolsbd said:**
> El Gnome Nanny ho pot fer:

Gràcies és just el què buscava

Lluís

---

