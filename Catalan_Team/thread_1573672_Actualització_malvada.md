---
title: "Actualització malvada?"
date: 2010-09-13
forum: Catalan Team
---

### Post by rosa d'abril on 2010-09-13
Feia temps que treballava amb l'Ubuntu 10.04 sense problemes, però ahir vaig actualitzar-lo i em passen coses estranyes. D'entrada se'm va penjar l'ordinador un parell de vegades, però el més greu és que quan m'obre alguna aplicació, la finestra no té els botons de minimització-restauració-tancament i a més me les obre enganxades al quadrant superior esquerra, amb la qual cosa em tapa la barra de tasques de l'Ubuntu (és obvi que no em deixa arrossegar la finestra).
Algú sap què li passa? Agrairé qualsevol suggeriment

---

### Post by lluisanunez on 2010-09-13
A mi em va passar això al fer l'upgrade a la nova versió.  Vaig solucionar-ho així:

[LIST]
[*]tancant el compiz (desactivant els efectes d'escriptori), sortint de la sessió i tornant a entrar. Hi ha un programet **compiz-switch** als repos que pot ser útil
[*]actualitzant el driver de Nvidia (quina tarja gràfica tens?)
[*]la finestra que "tapa" la pots moure prement la tecla Alt i agafant la finestra pel mig (no per la barra)
[/LIST]

---

### Post by rosa d'abril on 2010-09-13
Gràcies, Lluïsa,
Prenc nota del tercer consell, que em serà molt útil. Ara bé, què faig per desactivar el Compiz? (Suposo que se'm nota que no hi entenc gaire).
Quant a la targeta gràfica, t'ho diré aquesta tarda.
Salut!

---

### Post by wgarcia on 2010-09-13
Per desactivar el Compiz, ves al menú Preferències, escull Aparença, aquí escull Efectes visuals, i marca "Cap".

---

### Post by rosa d'abril on 2010-09-13
A veure, engego la màquina i em diu que fa unes comprovacions per tal de detectar si el disc dur està malmès. Em diu que sí i que premi F per si vull arreglar-ho. Després de bastant estona m'engega l'Ubuntu però a l'escriptori em surten unes lletres petites i negres d'origen desconegut que no sé com treure. Obro el Firefox i intento moure la finestra (sense botons) de la manera que la Lluïsa m'apuntava. Ni cas. 
Faig el que em diu wgarcia per desactivar el Compiz i resulta que a Aparença no m'apareix Efectes visuals. Quin desastre. Per altra banda, com puc saber quina tarja gràfica tinc? I, finalment, vaig a provar si trobo el compiz-switch als repos, a veure què passa.
Gràcies per la paciència.

---

### Post by rosa d'abril on 2010-09-13
Perdoneu, rectifico. Sí he trobat això d'Efectes Visuals però ja diu "Cap". A més, he descobert que no em llegeix els arxius en PDF que tinc a l'escriptori. Us n'envio una imatge. 
Alguna idea sobre com aconseguir tancar, moure o minimitzar les finestres?
Gràcies de nou

---

### Post by rosa d'abril on 2010-09-14
Hola, companys,

Ja està tot solucionat. Simplement me'n vaig anar al gestor de paquets, vaig veure quins hi havia instal·lats que fessin referència a l'escriptori i els vaig reinstal·lar.

Gràcies

---

### Post by SiscoGarcia on 2010-09-16
> **rosa d'abril said:**
> Ja està tot solucionat.

Doncs per fer-ho del tot bé, ara cal que marques el fil com a resolt: ves a «Thread Tools», ho desplegues i selecciones «Mark this thread as solved», així qui vinga darrere amb un problema com el teu veurà que pot trobar-hi una solució ;)

---

