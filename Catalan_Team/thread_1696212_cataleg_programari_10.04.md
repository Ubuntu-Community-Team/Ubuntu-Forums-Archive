---
title: "cataleg programari 10.04"
date: 2011-02-27
forum: Catalan Team
---

### Post by venusfenix on 2011-02-27
buenas,

acabo d'actulitzar-me a 10.04, a part un problema de nvidia, estic instal.lant altres programes i no em deixa fer res, en dona un missatge que el programari no es de confiança.

Gracies,

---

### Post by wgarcia on 2011-02-27
Pots enganxar el missatge exacte que et dóna i quan te'l dóna?

---

### Post by venusfenix on 2011-02-27
doncs quan intento instal.lar qualsevol programa nou, al portar un 3%, surt:

Requereix la instal·lació de paquets que no són de confiança

Aquesta acció requereix la instal·lació de paquets de fonts no autenticades.

i para l'instal.lació.

??

---

### Post by venusfenix on 2011-02-27
estic experimentant que molts programes que ja tenia instal.lats, ara amb 10.04 han deixat de funcionar.
potser que tot sigui degut al mateix probleme?


Per mes info, tinc la versio 64 bits, j'ha m'havia actualitza't en un altre ordinador a 10.04 i sense cap probleme, veig que el comportament no es el mateix, inclus estic fen proves d'instal.lar el mateix programa en el dos ordinadors, pel terminal, i el comportament es diferent, em sembla que la causa esta en el repositoris.

he intentat anar a Sistema, Administració,  fonts de programari i tampoc funciona.

gracies,

---

### Post by wgarcia on 2011-02-27
Pel missatge que et donava en un altre fil, és possible.

Això que et diu que hi ha paquets no autentificats és que et falta afegir les signatures d'aquests paquets. 

Hi ha un petit programa que baixa les signatures que et falten i que pot arreglar aquest problema que tens. 

Per instal·lar-lo has d'obrir una terminal i entrar aquestes comandes successivament:

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys

sudo launchpad-getkeys


a veure si hi ha sort.

---

### Post by venusfenix on 2011-02-27
Sembla que tot funciona, ja puc instal.lar sense problemes,

moltes Gracies, Wgarcia!!

---

### Post by wgarcia on 2011-02-28
Si li pots posar al fil "Solved" utilitzant "Thread tools" pot ser d'utilitat per si a algú altre li passa.

---

