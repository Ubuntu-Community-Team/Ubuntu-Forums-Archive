---
title: "Formatejar nou disc dur desde un USB Kubuntu"
date: 2012-03-02
forum: Catalan Team
---

### Post by lluisalguero on 2012-03-02
Hola companys,

tinc un portàtil on em va petar el disc dur i n'he colocat un altre. Intento instal·lar Kubuntu desde un USB i a la primera pantalla em fica que no hi ha "espai disponible", pel que suposo que haig de formatejar primer el disc dur. Com un ho puc fer això? Algún comandament via consola?

Moltes gràcies per l'ajuda.

Lluís

---

### Post by wgarcia on 2012-03-03
Però tens alguna cosa en aquest nou disc dur o és nou de trinca?

---

### Post by lluisalguero on 2012-03-08
> **wgarcia said:**
> Però tens alguna cosa en aquest nou disc dur o és nou de trinca?

Nou de trinca

---

### Post by akyra on 2012-03-08
En el Ubuntu quan vols instal·lar-lo pots elegir si en l'espai que queda o fer-ho de forma manual, si elegeixes aquesta ultima opció t'apereixarà una opció per poder formartejar i fer les particions que et calguin.
Suposo que a Kubuntu ha de ser igual, no?

Salutacions.

---

### Post by lluisalguero on 2012-03-08
> **akyra said:**
> En el Ubuntu quan vols instal·lar-lo pots elegir si en l'espai que queda o fer-ho de forma manual, si elegeixes aquesta ultima opció t'apereixarà una opció per poder formartejar i fer les particions que et calguin.
Suposo que a Kubuntu ha de ser igual, no?

Salutacions.

Quan intento instal·lar em demana: que estigui connectat a internet, al corrent elèctric i 3GB (ho dic de memòria) d'espai al disc dur. A partir d'aquí no em deixa avançar

---

### Post by akyra on 2012-03-09
Hola lluisalguero,

He estat veient un video d'instal·lar kubuntu, i veig que és practicament el mateix de ubuntu, i el que et demana són uns requeriments mínims, que entre ells hi ha els 3.8GBytes de disc. Quan arribes a aquest punt has provat a fer "Endavant"? (Sí, ja ho sé que sembla tonto)
Si fas "Endevant" t'hauria de sortir la pantalla per poder asignar espai al disc i particionar el disc com tu vulguis. És aquí a on podràs elegir el que necessites i fer les particions que vulguis amb el disc dur. Crec que el millor és seleccionar "Manual" i dimensionar les particions.

Et deixo el link del video:
[http://www.youtube.com/watch?v=tucw1QBhcpE]("http://www.youtube.com/watch?v=tucw1QBhcpE")

Diguem que tal va.

Salutacions.

---

### Post by lluisalguero on 2012-03-09
> **akyra said:**
> Hola lluisalguero,

He estat veient un video d'instal·lar kubuntu, i veig que és practicament el mateix de ubuntu, i el que et demana són uns requeriments mínims, que entre ells hi ha els 3.8GBytes de disc. Quan arribes a aquest punt has provat a fer "Endavant"? (Sí, ja ho sé que sembla tonto)
Si fas "Endevant" t'hauria de sortir la pantalla per poder asignar espai al disc i particionar el disc com tu vulguis. És aquí a on podràs elegir el que necessites i fer les particions que vulguis amb el disc dur. Crec que el millor és seleccionar "Manual" i dimensionar les particions.

Et deixo el link del video:
[http://www.youtube.com/watch?v=tucw1QBhcpE]("http://www.youtube.com/watch?v=tucw1QBhcpE")

Diguem que tal va.

Salutacions.

El problema es que el botó "Endavant" està desabilitat :(. Miraré si em surt l'opció de fer-ho en manual.

Moltes gràcies per l'ajuda

---

### Post by akyra on 2012-03-11
Hola Luis, i formatejar abans el disc?
Podries iniciar el Kubuntu amb el CD en mode de live CD i una vegada a dins intentar-lo instalar.
Són solucions tontes, però no entenc perquè està deshabilitada l'opció de avançar, ja que l'unic que et diu són recomanacions.

Salutacins.

---

### Post by Miquel Ubuntero on 2012-03-11
Bones.
Si es tracta d'un disc nou de trinca és normal que no puguis abançar en la insta&#320;lació. Un missatge et diu que no hi ha prou espai, però el que realment passa és que, a més de no haber prou espai, el disc nou no deu de tindre tabla de particions.
Aleshores, amb un LiveCD, inicia'l i utilitza un editor de particions per: 1er crear una nova Taula de particions al disc (per exemple que sigui de msdos), 2on formatar el disc dur. Tot seguit podrás iniciar la insta&#320;lació sense problemes.
Una cosa més. No recordo quin programa inclou al Kubuntu per editar particions. Ara estic amb un Xubuntu i no ho puc mirar. 
Si utilitzes un LiveCD d'Ubuntu, hi té de serie el Gparted que és molt senzill.
Ja que tens intenció de provar Kubuntu, pot ser t'ajudarà aquesta guia:
[http://ca.wikibooks.org/wiki/Guia_Ubuntu/%C3%8Dndex_Kubuntu_12.04](http://ca.wikibooks.org/wiki/Guia_Ubuntu/%C3%8Dndex_Kubuntu_12.04)

Ben cordialment,
Miquel.

---

### Post by lluisalguero on 2012-03-11
Gràcies Akira i Miquel.

Miquel, miraré això que em dius quan tingui el portàtil disponible, ara el tinc mig desmontat en espera de que m'arribi la pasta tèrmica per a la CPU.

Ja fa temps que faig servir Ubuntu/Kubuntu, ara el vull ficar a un portàtil que tinc vell per a la dona :lolflag:

---

### Post by Miquel Ubuntero on 2012-03-11
Hola de nou.
Ja que no tinc gaire son :) he reiniciat el PC amb Kubuntu. 
He vist que la nova versió 12.04 porta un Gestor de particions del KDE al menú Aplicacions - Sistema. En aquest programa, a la pestanya Dispositiu hi tens l'accés a Nova taula de particions.

Un últim suggeriment. Ja que has parlat d'un ordinador vell, ha pensat en una distro més "lleugera"?
Si amb Kubuntu et tira bé, perfecte. Però si veus que et va lent, mira't el Xubuntu. Jo el gasto i n'estic molt satisfet.
En aquest enllaç trobaràs guies de Xubuntu, Ubuntu i d'altres (perquè puguis ampliar informació): [http://ca.wikibooks.org/wiki/Guia_Ubuntu](http://ca.wikibooks.org/wiki/Guia_Ubuntu)
Salutacions cordials,
Miquel.

---

### Post by akyra on 2012-03-12
Hola Miquel,

Respecte al que dius en el e-mail:
> Bones.
Si es tracta d'un disc nou de trinca és normal que no puguis abançar en la insta&#320;lació. Un missatge et diu que no hi ha prou espai, però el que realment passa és que, a més de no haber prou espai, el disc nou no deu de tindre tabla de particions.
entenc que ho fa des de un LiveCd (o USB), sinó com ho fas?
Per això jo deia, que quan fas "Endevant", aniries a poder elegir la forma "Manual" que podries crear una nova taula de particions, el problema és que no deixa tirar endevant per poder fer-ho manualment, això és el que m'extranya, de fet l'instalador encara no sap a on vols instalar Kubuntu.

Interesant saber com acaba. 

Salutacions

---

### Post by lluisalguero on 2012-03-12
> **Miquel Ubuntero said:**
> Hola de nou.
Ja que no tinc gaire son :) he reiniciat el PC amb Kubuntu. 
He vist que la nova versió 12.04 porta un Gestor de particions del KDE al menú Aplicacions - Sistema. En aquest programa, a la pestanya Dispositiu hi tens l'accés a Nova taula de particions.

Un últim suggeriment. Ja que has parlat d'un ordinador vell, ha pensat en una distro més "lleugera"?
Si amb Kubuntu et tira bé, perfecte. Però si veus que et va lent, mira't el Xubuntu. Jo el gasto i n'estic molt satisfet.
En aquest enllaç trobaràs guies de Xubuntu, Ubuntu i d'altres (perquè puguis ampliar informació): [http://ca.wikibooks.org/wiki/Guia_Ubuntu](http://ca.wikibooks.org/wiki/Guia_Ubuntu)
Salutacions cordials,
Miquel.

Quan dic vell, vull dir què té pot ser 4-5 anys. Ja sé sap com va això de la tecnologia...suposo que el Kubuntu l'aguantarà bé, com a alternativa provaria el Xubuntu.

---

