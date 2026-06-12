---
title: "Problemes d'inici"
date: 2007-06-12
forum: Catalan Team
---

### Post by Curial on 2007-06-12
Bentrobats.

He instal·lat l'ubuntu en un Pentium IV amb 512Mb sense cap tipus de problema.

La cosa ha canviat quan ho he intetentat en un Pent.III amb 256 Mb. He tingut algun contratemps.

No se per quin motiu l'aparença dels menus és diferent al del primer.

El cas és que no m'obre algunes aplicacions, l'open office és una d'elles o quan intento visualitzar  els arxius com a llista em queda la finestra buida, només és possible veure els arxius com a icones els axius com a icones.

Paga la pena reinstal·lar o es pot solucionat de manera més fàcil?

Gràcies.

---

### Post by Curial on 2007-06-13
Llegint un altre fil del forum he decidit reinstal.lar.

Vull tenir com a segon SO windows  i havia instal·lat únicament Ubuntu.

L'únic que em pica la curiosistat és perquè tinc una apareça diferent al obrir els menus,
es a dir, en el Pent.III no em surten icones. També em surt a l'escriptori una icona que posa ordinador, que amb el Pent.IV no em sortia.

Gràcies d'antuvi.

---

### Post by AlexMuntada on 2007-06-16
Pot ser el procés d'instal·lació detecta que tens poca memòria i decideix canviar el tema predeterminat per un altre que consumeixi menys recursos, amb menys icones.

Pots comprovar si el teu tema predeterminat és el Crux?

---

### Post by Curial on 2007-06-17
Efectivament, estic tenint problemes amb la RAM. 
Els haig de solucionar.
Gràcies.

---

### Post by Curial on 2007-06-20
> **AlexMuntada said:**
> Pot ser el procés d'instal·lació detecta que tens poca memòria i decideix canviar el tema predeterminat per un altre que consumeixi menys recursos, amb menys icones.

Pots comprovar si el teu tema predeterminat és el Crux?


Bé, sembla que el problema amb la memòria l'he resolt. Faig la instal·lacio, una mica lenta això sí, però s'instal·la correctament. Quan reinicio l'ordinador veig que la opció de "Ubuntu, kernel 2.6.20-16-generic" no m'apareix. trio la "Ubuntu, kernel 2.6.20-15-generic". Tot sembla estar correctament. 
Quan l'ubuntu s'actualitza veig que carrega alguna cosa referida al "Ubuntu, kernel 2.6.20-16-generic"  i em dona un error a l'acabar l'actualització:

(E: gnome-app-install: el subprocés post-installation script retornà el codi d'eixida d'error 139 
E: linux-restricted-modules-2.6.20-16-generic: el subprocés post-installation script retornà el codi d'eixida d'error 139 
E: linux-restricted-modules-generic: problemes de dependències - es deixa sense configurar 
E: linux-generic: problemes de dependències - es deixa sense configurar )

A partir d'aqui ja no em surten les icones al costat de cada opció i a l'escriptori m'apareix la icona ordinador i la de papera.

Quan he intentat veure el Sistema-Preferències-Tema surt aquest missatge:

(No s'han trobat els esquemes de temes predeterminats en aquest sistema. Això vol dir que provablement el metacity no està instal·lat, o que el gconf no està configurat correctament.)

Intento instal·lar l'amor i el gnome-thmes-extras i torna a sortir un altre error:

(E: linux-restricted-modules-2.6.20-16-generic: el subprocés post-installation script retornà el codi d'eixida d'error 139
E: linux-restricted-modules-generic: problemes de dependències - es deixa sense configurar
E: linux-generic: problemes de dependències - es deixa sense configurar)

Per cert, he mirat en un altre ordinador que em funciona amb ubuntu i si que surten les icones amb el tema "crux".

Com se si tinc el metacity instal·lat? i en tal cas, Com configuro el gconf?

Gràcies, i perdoneu pel rotllo.

---

