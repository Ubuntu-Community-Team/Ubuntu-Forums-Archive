---
title: "Karmic es congela en canviar d'usuari"
date: 2010-03-03
forum: Catalan Team
---

### Post by ximoberna on 2010-03-03
Estic comprovant que la Karmic es congela amb una pantalla negra quan s'intenta canviar d'usuari. En tinc tres en aquest ordinador. En altre només hi ha un d'usuari i passa el mateix. El qual té lògica, però també passa aquí tant quan l'escriptori és bloquejat com quan no.

Salutacions i gràcies per davant!

---

### Post by wgarcia on 2010-03-04
Tens els efectes visuals activats? (Aparença -> Efectes visuals) Quanta memòria RAM tens? 

És possible que els ordinadors que esmentes no tinguin prou memòria com per suportar dos usuaris amb els efectes visuals carregats (cosa que passa quan canvies d'usuari sense sortir de la sessió). Una cosa que pots provar doncs és posar Aparença -> Efectes Visuals -> Cap, a veure si així et deixa canviar d'usuari.

---

### Post by ximoberna on 2010-03-04
> **wgarcia said:**
> Tens els efectes visuals activats? (Aparença -> Efectes visuals) Quanta memòria RAM tens? 

És possible que els ordinadors que esmentes no tinguin prou memòria com per suportar dos usuaris amb els efectes visuals carregats (cosa que passa quan canvies d'usuari sense sortir de la sessió). Una cosa que pots provar doncs és posar Aparença -> Efectes Visuals -> Cap, a veure si així et deixa canviar d'usuari.

No serà per RAM! En té 4 Gigues...

Salutacions!

---

### Post by orestesmas on 2010-03-05
Jo m'he trobat amb un cas semblant, si no el mateix: A vegades no apareix el gestor d'accés (gdm, kdm, xdm...), ja sigui en inicial les X o en canviar d'usuari (moment en que el gestor d'accés també reinicia les X).

Per mi que deu ser un bug del xorg o del gestor d'accés qu euso jo (kdm).

De fet en el meu cas la màquina no està congelada perquè s'hi pot accedir via ssh, cosa que et permet reiniciar el gestor d'accés. No ha entrat en mode gràfic, però segons com també pots usar Ctrl-Alt-F1 per activar una consola i des d'allí reiniciar el gestor d'accés.

A mi no em passa sempre, només esporàdicament, i no en totes les màquines.

---

### Post by ximoberna on 2010-03-05
> **orestesmas said:**
> Jo m'he trobat amb un cas semblant, si no el mateix: A vegades no apareix el gestor d'accés (gdm, kdm, xdm...), ja sigui en inicial les X o en canviar d'usuari (moment en que el gestor d'accés també reinicia les X).

Per mi que deu ser un bug del xorg o del gestor d'accés qu euso jo (kdm).

De fet en el meu cas la màquina no està congelada perquè s'hi pot accedir via ssh, cosa que et permet reiniciar el gestor d'accés. No ha entrat en mode gràfic, però segons com també pots usar Ctrl-Alt-F1 per activar una consola i des d'allí reiniciar el gestor d'accés.

A mi no em passa sempre, només esporàdicament, i no en totes les màquines.

Com seria això de reiniciar el gestor d'accés?
```
start gdm
```

?? És el que jo vaig usant ara...

Salutacions i moltíssimes gràcies!

---

### Post by wgarcia on 2010-03-08
Seria:

sudo service gdm restart

---

