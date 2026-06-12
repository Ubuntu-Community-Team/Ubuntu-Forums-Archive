---
title: "Kernels antics, eliminats?"
date: 2009-04-03
forum: Catalan Team
---

### Post by Quepotser on 2009-04-03
Bon dia tothom. No sé si el titol es massa aclaridor, però no se m'ha acudit res més.
Tafanejant per l'ordinador m'he trobat al directori "/usr/src", apart del que es actiu, tots els kernels antics que creia que ja havia eliminat definitivament. Si clico "Propietats" em diu que tenen una colla de MB, vaja, que estàn ocupant un espai en el disc.
Es poden esborrar sense que passi res? i una altra pregunta: no s'ho carregava tot el "aptitude remove --purge"?
Algú podria informar-me?

---

### Post by indiosincracia on 2009-04-03
Cada cop que s'instal·la un nou kernel l'antic es queda expressament per si hi hagués algun problema amb el nou, si el nou et funciona pots desinstal·lar els antics amb el synaptic, busca linux-image-2.
també et desapareixeran del Grub.
Per saber quin kernel tens:
uname -r

---

### Post by Quepotser on 2009-04-03
Bona tarda. Gràcies per la resposta i perdona per haver fet de manera tan confosa la pregunta. Provaré d'arreglar-ho:

El kernel que estic utilitzant ara és l'últim que se'm va actualitzar: el 2.6.24.24.
Tinc de "reserva" el 2.6.24.23.
Els que jo creia que ja havia eliminat amb l'*aptitude*, i que encara són a */usr/src*, són el 2.6.24.19, 2.6.24.21 i el 2.6.24.22.

Tenen alguna utilitat aquests kernels?,
Els puc esborrar i així alliberar una mica d'espai al disc dur?
Ho pregunto per què els vaig esborrar amb el *"aptitude remove --purge"* i jo creia que amb aquesta ordre s'esborrava **tot**. Resulta que, si encara hi són: es per alguna cosa? o simplement que l'*aptitude* no ho esborra **tot**.

Buff!, no sé si he aclarit la pregunta o l'he enredat més encara.

---

### Post by PatrickVogeli on 2009-04-03
es possible que hi tinguis les carpetes dels headers??? Mira que no tinguis instal·lat cap paquet linux-headers- dels kernels que has esborrat.

salut!

---

### Post by Quepotser on 2009-04-04
Bon dia. Efectivament són els linux-headers del kernels esborrats.
Serveixen per alguna cosa?

---

### Post by PatrickVogeli on 2009-04-04
no, si els has esborrat ja no serveixen per a res. De fet, només serveixen per a compilar módulos nous per al kernel, per a res mes.

salut

---

### Post by Quepotser on 2009-04-05
Bon dia. No els havia esborrat encara, però si tan sols seveixen per a compilar mòduls nous acabaré fent-ho. No tinc en perspectiva compilar cap mòdul. Gràcies.

---

