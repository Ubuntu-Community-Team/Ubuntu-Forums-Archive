---
title: "[SOLVED] Kubuntu no engega"
date: 2007-07-30
forum: Catalan Team
---

### Post by noidartes on 2007-07-30
[CENTER][LEFT]Hola,

Tinc un problema. Quan intento arrencar el Kubuntu tot funciona ok fins que he de posar la contrassenya. La poso correctament i sembla que m'arranca la sessió pero es posa la pantalla negra un moment i em torna a demanar la contrassenya de nou, de manera que d'aqui no passa. 

Teniu alguna idea de què pot ser? Jo he pensat que potser no té prou espai ja que tenia el disc molt ple i l'ultim dia abans de parar-lo (es va parar correctament) la mula s'havia parat sola un parell de vegades i no vaig entendre el perquè. Aixi he pensat que potser el disc no té suficient espai lliure per engegar la sessió. 

Son només hipòtesis ja que com sabeu els meus coneixaments de Linux son ridiculs. He buscat per internet i no he sabut trobar res.

Em podeu donar un cop de mà? 

Salut![/LEFT][/CENTER]

---

### Post by benetj on 2007-07-30
Hola noidartes,

Possiblement el que et passa sigui que t'has quedat sense espai a la partició /

Intenta fer un *apt-get clean* per esborrar els paquets baixats quan has instal·lat o actualitzat el sistema.

Esper que et sigui  d'ajuda.

Salut,

---

### Post by noidartes on 2007-07-30
Que fàcil!  ;)   Problema solucionat!! Moltes gràcies.

Perquè no em torni a passar em podeu indicar on puc trobar l'espai que tinc lliure a la partició? He estat remenant i no ho sé veure.

Salut!

---

### Post by jmaspons on 2007-07-30
Per mirar l'espai de les particions pots fer servir la comanda df -h (diskfree -llegible per humans). Si vols pots instal·lar un programet que es diu Kdf que fa el mateix.

Salut!

---

### Post by noidartes on 2007-07-30
Fet, gràcies!!

---

### Post by benetj on 2007-07-30
Perdona per no haver contestat abans, veig que t'ho han resolt sense problemes.

Salutacions!

---

