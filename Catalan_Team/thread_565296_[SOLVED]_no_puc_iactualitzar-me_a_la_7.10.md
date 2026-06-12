---
title: "[SOLVED] no puc iactualitzar-me a la 7.10"
date: 2007-10-02
forum: Catalan Team
---

### Post by siscuboontu on 2007-10-02
Bon dia,

Tinc instal·lada la 7.04 amb l'automatix i vull actualitzar-me a la 7.10. No puc fer-ho perquè em dóna el missatge:
       "No ha pogut connectar amb www.getautomatix.com/apt/dists/feisty/..."

Després d'intentar-ho algunes vegades he decidit desinstal·lar el paquet automatix i he intentat tornar a actualitzar-me i m'ha tornat a sortir el mateix missatge.

He intentat actualitzar-me per consola i tampoc no he pogut perquè intenta buscar alguns paquets d'automatix, de manera que es queda sense actualitzar.

Què puc fer?

Gràcies.:confused:

---

### Post by papapep on 2007-10-02
L'únic consell que et puc donar és que et treguis de sobre l'Automàtix. No és una manera oficial de instal·lar programari i només porta que problemes, tot i que vagi bé pel tema de controladors de video i tal.

---

### Post by siscuboontu on 2007-10-02
Ja ho he intentat papapep, suposadament he desinstal·lat l'automatix però tampoc no puc actualitzar-me. Com puc fer per tal d'assegurar-me que m'he tret de sobre l'automatix?

---

### Post by Ferri on 2007-10-02
Has intentat fer?: ```
sudo update-manager -c -d
```
L'Automatix en principi es desinstal·la com qualsevol altre paquet, encara que no veig perquè no t'hauria de deixar actualitzar a Gutsy.
Potser no estaria de més que et miris el teu sources.list a veure si hi tens alguna entrada de l'Automatix i esborra-la o desactiva-la (posa un # al davant).
**Si actualitzes a la versió 7.10 (Gutsy), tingues present que és una beta i, per tant, pots trobar-te amb problemes inesperats**

---

### Post by RainCT on 2007-10-02
Segurament això ho arreglarà:

1. Prem Alt + F2
2. A la finestra que t'apareixerà, escriu: gksudo gedit /etc/apt/sources.list
3. Prem «Executa»
4. Cerca aquelles línies que facin referència a l'Automatix i esborra-les. Finalment guarda l'arxiu i des del Synaptic actualitza els llistats de paquets.

---

### Post by pespin on 2007-10-02
En RainCT té raó, pel que em sembla recordar al desinstal·lar automatix no s'esborren els repositoris del sources.list :)

---

### Post by siscuboontu on 2007-10-02
Per fi!!!!

Finalment fa una estona he aconseguit actualitzar-me a la versió 7.10, el que no acabo d'entendre què ha passat perquè ara hagi pogut actualitzar-me. L'únic que sé que he fet és desactivar el beryl. Ja havia provat amb Alt+F2 seguit de" update-manager -d" altres vegades, Ferri, i no me n'havia sortit però aquest cop sí. No he arribat a provar "gksudo gedit /etc/apt/sources.list" com proposaves, RainCT. De tota manera, moltes gràcies a tots.

Sisco.:)

---

### Post by siscuboontu on 2007-10-02
Per cert,

Suposo que s'hauria de dir que aquest fil està solventat, no?

---

### Post by papapep on 2007-10-02
Doncs pots fer-ho anant a l'enllaç "Thread Tools" i clica damunt l'opció "Mark thread as solved".
;-)

---

