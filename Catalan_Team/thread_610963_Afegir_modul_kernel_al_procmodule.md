---
title: "Afegir modul kernel al /proc/module"
date: 2007-11-12
forum: Catalan Team
---

### Post by cortsenc on 2007-11-12
En principi, he instal·lat correctament el modul fglrx però al carregar un script que el posi per omissió, em demana que no esta inclós a l'arxiu** /proc/module**, en canvi el tinc a l'arxiu /etc/module.

Que he de fer per tenir-lo en el primer arxiu?

Gràcies

---

### Post by papapep on 2007-11-12
Tot el que penja de /proc, són dades que els processos generen. Aleshores, a /proc/modules hi ha els mòduls que estan carregats en aquest moment.
"Pulutant", el que entenc és que No tens el mòdul carregat.

Fes un** lsmod** i veuràs si efectivament el tens carregat o no.

---

### Post by CarlesOriol on 2007-11-13
Usa l'envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cortsenc on 2007-11-14
gràcies als dos

---

