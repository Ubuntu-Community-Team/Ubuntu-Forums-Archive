---
title: "[SOLVED] Compartir impressora"
date: 2007-06-01
forum: Catalan Team
---

### Post by TotAmbA on 2007-06-01
Molt bones, no se si m'hauria de presentar abans de penjar un post...
Bé, fa uns pocs mesos que vaig instal.lar l'ubuntu 6.10 a un Pentium III amb 300 i pico MB de RAM. Fins aqui tot bé.
Fa poc, vaig aconseguier una impressora HP laserjet 1100, que no vaig tenir cap mena de problemes per instal.lar-la.
Tinc 2 PC's més en xarxa sota windows.
Tinc una carpeta compartida d'ubuntu a la qual poden accedir els 2 pc's que corren amb Windows (XP els 2) sense cap mena de problema.
Llavors, vaig llegir per algun post que per poder compartir la Laser havia d'habilitar dins d'impressores l'opcio (Detect Lan Printers i Share printers). Aquest últim no el puc habilitar ja que diu que m'obre el port 631 i pot ser perillós.
Llavors, vaig arrancar el windows, i per entorno de red vaig accedir a l'impressora de l'ubuntu i remotament es va instal.lar en el windows. Fins i tot, vaig poder fer una prova d'impressió.
PERO, desde windows si intento imprimir algun document de PDF, Word o qualsevol cosa que no sigui una prova de windows em dona error, com si no es pogués accedir a l'impressora.  Si miro l'estat de l'impressora en windows em diu HP LASERJET 1100 en ubuntu Acceso denegado, no se pudo establecer la conexión.

M'estic iniciant en això del Linux i el tema teclejar i modificar per terminal no el domino gaire, pel que busco quelcom senzill per poder compartir aquesta impressora. O si més no, entendre el que s'ha de fer i que no sigui molt complicat.
No se si hi ha algun post on ja es parla d'aquest tema però jo l'he intentat buscar i no he trobat gaire res.

Gràcies anticipades!

---

### Post by Ferri on 2007-06-03
Has intentat això (en anglès)?
[Impressió en xarxa a Ubuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")
Ara, si pel que dius, no vols obrir el port 631 ho veig complicat.
Lògicament, obrir qualsevol port pot ser teòricament perillós, però si estàs dins d'una xarxa i tens el router ben configurat, no hauria de ser un problema, ja que les úniques màquines que t'haurien d'accedir al 631 són les de la teva xarxa, que és d'esperar que siguin de confiança. Si realment et preocupa, hi ha alguns tallafocs que et poden ajudar per configurar qui i com et pot accedir a un port en concret, i també pots configurar CUPS de manera que només permeti accés a la impressora a màquines concretes. De totes maneres, insisteixo, el principal és tenir la porta d'entrada a la teva xarxa ben protegida (el teu router, o el que facis servir per accedir a la web).

---

### Post by nachocan on 2007-06-05
Jo estic imprimint amb una laserjet 1010, penjada d'un pc amb Ubuntu 7.04. 
Per fer-ho rutllar, he seguit les indicacions que hi ha a continuació:

[http://www.guia-ubuntu.org/index.php?title=Compartir_una_impresora_con_Windows_2000/XP](http://www.guia-ubuntu.org/index.php?title=Compartir_una_impresora_con_Windows_2000/XP)

Espero que et serveixi.

---

### Post by TotAmbA on 2007-06-07
Gràcies per les respostes.
Problema solucionat.
Al final remenant remenant, vaig trobar el CUPS, vaig configurar l'apartat d'administració compartint l'impressora per a altres equips.
Un cop vaig tenir el CUPS configurat, el problema estava en com configurar la impressora en windows (en el meu cas XP). Doncs bé, boto dret, afegir impressora, impressora de xarxa i seleccionem direcció URL. I que s'hi posa? doncs això: [http://192.168.1.100:631/printers/LaserJet-1100](http://192.168.1.100:631/printers/LaserJet-1100)
on LaserJet-1100 és el nom que li hem posat a l'impressora quan l'hem configurada a l'Ubuntu.

---

### Post by CarlesOriol on 2007-06-07
Però, però, però ...

A veure primer dius:

*Aquest últim no el puc habilitar ja que diu que m'obre el port 631 i pot ser perillós.*

i després dius:

*[http://192.168.1.100:](http://192.168.1.100:)**631**/printers/LaserJet-1100*

Potser no ho has entès, però el problema de la teva pregunta era com compartir la impressora SENSE obrir el port 631... i després en ensenyes que ho has fet.

No és un pel contradictori?

---

### Post by TotAmbA on 2007-06-07
Abans de configurar-la pel CUPS, si anava a "Sistema"+"Administració"+"'s'està imprimint"+ petanya "paràmetres Globals" i activava: "Detectar impressores LAN" i "Comparteix impressores" em mostrava per pantalla el missatge:** Enabling LAN printers sharing will open port 631 on your system. This exposes you to the risk of exploiting any security vulnerabilities of the printing system. Remote attackers could potentially gain access to your system with the privileges of the "cupsys" user.** i no s'habilitava...

Llavors configurava la làser al Pc amb plataforma Windows i em donava el problema ja comentat al primer post (no es pot accedir a impressora) i no podia imprimir.

Posteriorment vaig descobrir el CUPS i configurant-lo com he citat anteriorment he pogut configurar-la i fer-la funcionar correctament sense que em doni missatges erronis d'impressora inaccessible (per windows, eh).

No se si ara ha quedat mes clar.

I a partir d'aqui que cadascu faci el que li sembli convenient. A mi m'ha funcionat aixi, suposo que hi ha 1000 i una formes de configurar una impressora.

Sento haver-me explicat malament i espero que serveixi per algun futur usuari.

---

### Post by Ferri on 2007-06-08
El que vol dir el Carles és que, amb el que has fet, has obert el port 631 per a l'usuari cupsys, que és el que deies que no volies fer.
De totes maneres, no crec que hagis d'estar gaire preocupat pel risc que teòricament això podria suposar.

---

