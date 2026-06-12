---
title: "Coneixeu algún programa de fax?"
date: 2007-06-07
forum: Catalan Team
---

### Post by rajoar on 2007-06-07
Be, necessitaria poder rebre i enviar fax en kubuntu des del processador de textos i d'altres programes. Es a dir un programa que generi una impressora-fax a l'estil dels del finestres.
En coneixeu algún que funcioni be?...

---

### Post by Ferri on 2007-06-09
Potser això et pot servir:
[DialupAndFax]("https://help.ubuntu.com/community/DialupAndFax")
Tot i que l'efax-gtk que et diu segur que dependrà d'una colla de llibreries de GNOME...

---

### Post by benjami on 2007-06-10
HylaFax és molt bo.  Això sí, té prestacions de servidor [1] que fan més complicada la lectura de la documentació i configurar-lo.  Però s'ho paga, perquè un cop configurat està allà sempre fent feina sense fallar.  Fa un parell d'anys que no ha fallat a una SUSE que tenc aquí al costat.

Per a enviar és una impressora de xarxa més.  Quan reps un fax, pam: email al canto avisant.  

[1] fer de fax de moltes màquines a una xarxa local (Windows també), enviar emails amb els fax annexats en PDF als destinataris, passarel·la email-fax, SMS-fax, fax-SMS etc

---

### Post by rajoar on 2007-06-10
Moltes gràcies Benjamí pel teu interès. De totes formes ja t'hauràs adonat que sóc molt novell i no se ben bé què és el que haig de fer...
Podrias indicar-me, pas per pas, conm haig d'instal·lar-ho en una workstation perquè tingui el fax accessible des de les aplicacions?...

---

### Post by AlexMuntada on 2007-06-12
> **rajoar said:**
> Podrias indicar-me, **pas per pas**, conm haig d'instal·lar-ho en una workstation perquè tingui el fax accessible des de les aplicacions?

Instal·lar les aplicacions és la part senzilla si utilitzes les eines d'Ubuntu (Synaptic per a
GNOME i Adept per KDE, si no vaig errat); el que et comenta en Benjamí que costa més
és configurar el servidor d'Hylafax, i això suposo que ja ho tens documentat als manuals.

En qualsevol cas, si tu només vols enviar (no rebre) faxos, hi ha d'altres eines més senzilles
que utilitzen només el client d'Hylafax o alguna eina alternativa com efax.  Si aquest és el
teu cas, aleshores et pots instal·lar el gfax per a GNOME, per exemple.  Altrament, et caldrà
tenir una mica de paciència i estudiar la documentació del servidor d'Hylafax.

---

### Post by rajoar on 2007-06-16
Bé..., he avançat bastant en el tema del fax...
A veure..., he hagut de baixar-me el driver de pagament HSF (Conexant Modem) de la pàgina de Linuxant (el driver lliure de pagament no permet activar el fax). L'he instal·lat i... voila!..., ja tenim el windows modem-fax degudament reconegut... M'he instal·lat també l'efax (l'hylafax el trobo molt complicat de configurar), l'he configurat i ja tinc l'efax preparar per rebre fax correctament... Efectivament puc rebre fax perfectament, sense cap problema...
Ara bé, encara no se ben bé com puc enviar fax des de, per exemple, l'OpenOffice... Acostumat al finestres dels k...... ,no se que haig de configurar perquè em surti una impessora fax dins dels programes, des d'on puguer-los enviar...
Només aconsegueixo, des de l'efax, reclamar el fitxer préviament guardat i enviar-lo com un fitxer postscript...
Crec que hauria d'èsser possible enviar-los des de qualsevol aplicació, no?..., però per moltes voltes que hi dono no trobo la sol·lució...
És a dir i tornant al començament..., he avançat bastant però encara em manca una miqueta..., a veure si algú m'ho acaba d'aclarir...
Gràcies a tots

---

### Post by AlexMuntada on 2007-06-16
Una solució bastant habitual per a integrar aquest tipus de coses a qualsevol aplicació passa per crear una impressora especial que faci l'enviament del fax enlloc d'imprimir el document.

Ara, no em preguntis pas com es fa perquè no en tinc cap idea.  Però segur que si busques alguna cosa en aquest sentit trobaràs el que vols fer.

---

