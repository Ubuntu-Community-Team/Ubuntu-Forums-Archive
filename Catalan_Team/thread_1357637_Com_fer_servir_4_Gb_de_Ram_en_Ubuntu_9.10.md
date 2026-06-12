---
title: "Com fer servir 4 Gb de Ram en Ubuntu 9.10"
date: 2009-12-17
forum: Catalan Team
---

### Post by lluisalguero on 2009-12-17
Buscant informació sobre la meva tarja wifi, he trobat la forma de que la Karmic Kola em reconegui els 4 Gb de RAM.

```
sudo apt-get install linux-server linux-headers-server
```

De moment no té "efectes secundaris", i espero que continue igual.

Donar les gràcies a papapep, ja que un comentari a un post meu hem va "iluminar". Moltes gràcies papapep

[http://ubuntuforums.org/showpost.php?p=8340720&postcount=9](http://ubuntuforums.org/showpost.php?p=8340720&postcount=9)

---

### Post by sordoman on 2009-12-18
Hola,
Si no estas usant, ubuntu 64bits jo et recomanaria buscar el kernel amb l'extensió "PAE" ho pots trobar a synaptic sense problemes hauries de buscar 2.6.31-15-generic-pae o alguna cosa semblant depent del kernel que estiguis utilitzant

Pots posar a un terminal
```

uname -r

```

i buscar a synaptic el mateix nucli pero acabat amb "pae"

sort!!):P

---

### Post by lluisalguero on 2009-12-18
> **sordoman said:**
> Hola,
Si no estas usant, ubuntu 64bits jo et recomanaria buscar el kernel amb l'extensió "PAE" ho pots trobar a synaptic sense problemes hauries de buscar 2.6.31-15-generic-pae o alguna cosa semblant depent del kernel que estiguis utilitzant

Pots posar a un terminal
```

uname -r

```

i buscar a synaptic el mateix nucli pero acabat amb "pae"

sort!!):P

Fent el descrit anteriorment tinc instal·lat el 2.6.31.16-generic-pae

---

