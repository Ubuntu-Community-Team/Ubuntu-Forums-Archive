---
title: "Portatil no detecta DVD"
date: 2011-09-22
forum: Catalan Team
---

### Post by sakuraya on 2011-09-22
Tinc un portàtil HP530 del 2008 el qual venia amb Windows instal.lat; de seguida vaig fer els 2 CD Recovery i vaig formatar per instal.lar Ubuntu. Darrerament havia detectat que el DVD no funcionava: s'obre i es tanca, es sent soroll de què llegeix, però res més. 
No hi havia tornat a pensar perquè habitualment no l'he necessitat, sempre treballo amb USB, però ara l'he tornat a formatar per instal.lar Ubuntu 11.04.
La qüestió es que a l'intentar instal.lar-lo, m'he trobat amb aquest problema, que de moment he solventat fent un pen USB per instal.lar Ubuntu, i així estic ara.
Però de cap manera trobo per "activar" el DVD. Per les comprovacions que he fet, crec que deu ser alguna cosa de la Bios. No hi entenc gaire, però he provat un munt de coses: instal.lar Wine per intentar crear USB amb els Drivers de la placa mare penjats a la web del fabricant, modificar l'ordre de lectura de la Bios a l'arrencar,... però crec que el problema vé que ja desde que s'engega la màquina, no l'"activa". 
Disposo d'un altre PC de suport amb Windows i Ubuntu, per si cal, i al portàtil només d'Ubuntu amb internet (de fet, voldria crear una petita partició per a un Windows :(, doncs hi ha algun programari que amb Wine no em funciona).

Creieu que em podeu donar un cop de mà? Ja no sé per on escapar.
Moltíssimes mercès.
Salut.

---

### Post by wgarcia on 2011-09-22
Mira de posar algun disc al lector DVD, i des d'una terminal entrar l'ordre 

dmesg

i veure si surt algun missatge d'error que sembli relacionat amb el lector DVD a les últimes línies que sortiran a la pantalla d'aquesta ordre. Això pot donar una pista.

---

### Post by sakuraya on 2011-09-22
Primer de tot mercès.

Insereixo l'enllaç a l'arxiu resultant de l'ordre.

No ho sé interpretar, però aparentment sembla com si hi hagués algun conflicte entre el DVD i el mòdem-USB? És possible?

---

### Post by sakuraya on 2011-09-22
També comentar que he provat re-inicialitzant sense connectar el mòdem, ni cap altre element que vagi amb l'USB.

---

### Post by wgarcia on 2011-09-23
La pròxima vegada sisplau enganxa els resultats en un fitxer i adjunta el fitxer. 

Pel que em sembla no hi ha cap referència a aquest DVD en el que mostres. Has posat un disc abans d'executar "dmesg"? Si hi hagués alguna cosa útil estaria al final, "dmesg" recull els missatges del sistema i si el DVD produeix un error es podria veure alguna cosa. 

És un DVD extern o, segons el que comentes, es connecta per USB? En aquest cas l'operació podria ser desendollar i endollar el DVD i després mirar les últimes línies del dmesg.

---

### Post by sakuraya on 2011-09-23
Gràcies. Disculpes pel llistat, ja l'he substituït per arxiu adjunt.

En el moment d'executar l'ordre, efectivament hi havia un DVD posat. Com sempre, al moment de posar-lo, es nota que roda per llegir, però no fa res més.

No es tracta de cap aparell extern, es el lector/gravador que duia incorporat d'origen el propi portàtil. El que sí que connecto per USB es el mòdem.

---

### Post by wgarcia on 2011-09-25
El que deia és engegar l'ordinador sense cap disc a la unitat de DVD. Un cop que arribes a l'escriptori, posar un DVD, i mirar les últimes línies del dmesg a veure si es veu alguna referència a la unitat de DVD o algun tipus d'error reportat.

---

### Post by sakuraya on 2011-10-02
Gràcies. Aquí adjunto dos documents, un abans de posar cap disc, i l'altre tornant a donar l'ordre després d'haver-ne posat un.

---

### Post by wgarcia on 2011-10-02
Segons el que es veu al "dmesg" no detecta cap activitat al disc. Has provat de iniciar un USB "Live", és a dir sense instal·lar, i mirar si detecta la unitat? Per crear-te un USB "live" a la pàgina de descàrrega de l'Ubuntu hi ha les instruccions, tot i que sembla que te l'has creat segons dius en missatges anteriors.

---

### Post by sakuraya on 2011-10-02
Sí, després de formatar el disc, al veure que no detectava la unitat, ja vaig haver d'instal.lar l'Ubuntu a partir d'un USB. Suposo que quan dius un USB "Live" et refereixes a això. Per cert, amb l'antiga versió que tenia instal.lada, la 8.10 (he fet el salt directament sense passar per la 9.XX), tampoc me'l detectava.

---

### Post by wgarcia on 2011-10-02
Recapitulant, et funcionava amb una versió antiga d'Ubuntu i et va deixar de funcionar amb la 8.10 i posteriors? No et funciona tampoc amb la 11.04 iniciada en mode "live" des de l'USB? 

Un altre suggeriment: prova d'instal·lar un programeta que es diu "lshw" (des del Centre de Programari o com estiguis acostumat a instal·lar els programes). Un cop instal·lat en un terminal fer:

sudo lshw > maquinari.txt

i adjunta aquest fitxer a un missatge.

Aquest programa fa un llistat complet del maquinari que hi ha (i que detecta) al teu ordinador, potser es pugui veure alguna altra cosa amb aquest recurs.

---

### Post by sakuraya on 2011-10-02
Efectivament, abans funcionava el DVD.

He instal.lat el programa, i adjunto el text que surt.

Mercès.

---

### Post by wgarcia on 2011-10-03
D'acord. La comanda que et vaig comentar va generar un fitxer "maquinari.txt" que podries haver adjuntat directament, però ja es veu en el que has adjuntat.

Mirant el que es veu, efectivament no hi ha referència al DVD, però si a una unitat de "cdrom" que sospitosament també diu HUAWEI, i aquesta és la marca normalment dels mòdems USB. Per tant una conjectura és que el sistema està muntant el mòdem USB com una unitat de CDROM (et funciona com a mòdem), però no sé si això inferirà amb la unitat de DVD, penso que no. 

A mi em sembla que pot haver-hi algun problema de maquinari amb la unitat de DVD, tens alguna evidència que funcioni (en alguna altra distribució, funcionava fins a una actualització, o coses així)?

---

### Post by sakuraya on 2011-10-05
Tal com efectivament dius, Huawei es la marca del modem usb que estic utilitzant.

En quant a què el DVD hagués funcionat alguna vegada, efectivament, en alguna versió més antiga sí que funcionava, però no recordo en quina. Això que em comentes m'ha fet pensar que potser seria una bona idea recuperar i instal.lar una altra versió més antiga, aprofitant que seria ràpid ja que ara no tinc dades a salvaguardar. D'aquesta manera segurament podríem descartar altres qüestions.

Com que es ràpid, ho provo i dic quelcom.

Moltes mercès.
Salutacions.

---

