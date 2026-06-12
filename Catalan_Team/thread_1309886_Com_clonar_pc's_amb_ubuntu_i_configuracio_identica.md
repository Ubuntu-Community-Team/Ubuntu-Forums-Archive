---
title: "Com clonar pc's amb ubuntu i configuracio identica?"
date: 2009-11-01
forum: Catalan Team
---

### Post by Lotiopep on 2009-11-01
Hola a tothom.

Des de fa un parell d'anys que utilitzo ubuntu amb exit. A mes d'instal.lar-lo en maquines meves tambe l'he instal.lat en dos ordinadors de l'academia on treballo. Els ha agradat tant que s'esta generant un projecte entre l'academia i l'ajuntament per crear una sala d'ordinadors amb programari lliure oberta al public en general. Els meus coneixements informatics son limitats i basats, sobretot, en l'experiencia d'haver instal.lat ubuntu en uns quants pc's (i haver-me barellat amb els drivers, sobretot). Es per aixo que us demano ajut pel seguent:
 
1. Soc jo que he de demanar la configuracion de hardware del ordinadors. Per la meva experiencia, se que no cal molta maquina per correr ubuntu sense problemes de rendimdent. Estic pensant a demanar un processador intel o AMD d'un sol nucli, crec que 1 GB de RAM es suficient per als propers anys (ara estic escrivint des del meu portatil que te nomes 256 MB amb l'ubuntu 9.10), pero quina tarjeta grafica? ATI, Nvidia, models que no donguin problemes amb el driver?

2. Com que tots els ordinadors seran identics, havia pensat en instal.lar-ho tot en un primer pc (ubuntu 9.10, aplicacions, idioma, fons de pantalla i tema, ...) i a partir d'aquest clonar els altres (creant una mena de distribucio amb un dvd). D'aquesta manera m'estalviaria molt de temps baixant, instal.lant i configurant tot el que no ve per defecte amb el cd d'instal.lacio d'ubuntu (vlc, configuracio del compiz, codecs, ...). Es possible aixo? (cal tenir en compte els meus escassos coneixements informatics). Veig que hi ha l'Ubuntu Customization Kid, pero no se si es exactament el que jo pretenc.

3. Per evitar qualsevol tipus de problema legal (ja que serien ordinadors publics) em fa por que l'ubuntu-restricted-extras i la resta de codecs i fonts no siguin realment legals. Ho son? Cal pagar algun tipus de llicencia?

Moltes gracies per la vostra ajuda.

---

### Post by PatrickVogeli on 2009-11-01
si es per fer treballs d'ofimatica, internet i demes, jo tiraria amb algun processador de doble nucli d'Intel (un E4300 per exemple), 2gb de ram, 160gb de disc dur i amb una placa base amb el conjunt de xips Intel, així com gràfica integrada intel també.

Respecte a l'ubuntu-restricted-extras: diria que aqui es legal. Als EUA em sembla que no, pero aqui cap estic quasi segur que cap problema.

Salut

---

### Post by papapep on 2009-11-01
> 1. Soc jo que he de demanar la configuracion de hardware del ordinadors. Per la meva experiencia, se que no cal molta maquina per correr ubuntu sense problemes de rendimdent. Estic pensant a demanar un processador intel o AMD d'un sol nucli, crec que 1 GB de RAM es suficient per als propers anys (ara estic escrivint des del meu portatil que te nomes 256 MB amb l'ubuntu 9.10), pero quina tarjeta grafica? ATI, Nvidia, models que no donguin problemes amb el driver?

Intel no et portarà cap problema, Nvidia és probable que tampoc i ATI és probable que te'n porti. Feu el que feu, **és imprescindible** assegurar la jugada buscant referències sobre el ferro que es compra abans, per no pifiar-la.

> 2. Com que tots els ordinadors seran identics, havia pensat en instal.lar-ho tot en un primer pc (ubuntu 9.10, aplicacions, idioma, fons de pantalla i tema, ...) i a partir d'aquest clonar els altres (creant una mena de distribucio amb un dvd). D'aquesta manera m'estalviaria molt de temps baixant, instal.lant i configurant tot el que no ve per defecte amb el cd d'instal.lacio d'ubuntu (vlc, configuracio del compiz, codecs, ...). Es possible aixo? (cal tenir en compte els meus escassos coneixements informatics). Veig que hi ha l'Ubuntu Customization Kid, pero no se si es exactament el que jo pretenc.

Tens el [clonezilla]("http://clonezilla.org/"), que és un livecd que et permet clonar tant discs sencers com particions en concret. Com que dius que muntareu màquines iguals, crec que és la millor opció.

També pots instal·lar la distribució a totes les màquines, a una instal·lar tots els paquets necessaris i a la resta instal·lar-los a partir d'emprar el "dkpg --set-selections" i el "dpgk --get-selections", però això és més feina, clar.

> 3. Per evitar qualsevol tipus de problema legal (ja que serien ordinadors publics) em fa por que l'ubuntu-restricted-extras i la resta de codecs i fonts no siguin realment legals. Ho son? Cal pagar algun tipus de llicencia?

No crec que hi hagi cap problema en aquest sentit. El programari pot no ser especialment "lliure", però això no implica problemes de llicències, excepte que s'especifiqui de manera explícita.

---

### Post by Lotiopep on 2009-11-02
Tanta maquina? Havia pensat que una de les aventatges que podiem vendre a l'ajuntament era que no calia tenir un pc a "l'ultima" i, per tant, sortir-los mes barat. Tambe, ara que hi penso, el que tu em proposes ja no es precisament un ordinador a "l'ultima" :-) Possiblement es poden trobar baratets. Ho proposare.

---

### Post by Lotiopep on 2009-11-02
Em mirare aixo del clonezilla i com fer-lo anar. 

Moltes gracies a tots per les respostes.

---

### Post by SiscoGarcia on 2009-11-04
> **Lotiopep said:**
> Tanta maquina? Havia pensat que una de les aventatges que podiem vendre a l'ajuntament era que no calia tenir un pc a "l'ultima" i, per tant, sortir-los mes barat. Tambe, ara que hi penso, el que tu em proposes ja no es precisament un ordinador a "l'ultima" :-) Possiblement es poden trobar baratets. Ho proposare.

Realment no cal tanta màquina. Jo treballo a un institut i hem fet compres d'ordinadors de segona mà que corren perfectament amb ubuntu. Els hem comprat a botigues on-line que es dediquen a vendre els que fan anar empreses que fan compres en pla leasing o renting, i pots trobar veritables xollos. Ara ja estan sortint Pentium Dual Core a 2.8 GHz amb 2 o 4 GB de RAM per uns 200 € més IVA i ports, a part el monitor (que també pots trobar de segona mà). Això de marques reconegudes.

En el cas d'[inforocasión]("http://www.inforocasion.com/") i [ibericainfocomputer]("http://info-computer.com/index.php?option=com_content&task=view&id=1&Itemid=40"), que són les que conec, fins i tot pots tenir garantia d'un any.

---

### Post by pauelmaco on 2009-11-04
> **Lotiopep said:**
> Tanta maquina? Havia pensat que una de les aventatges que podiem vendre a l'ajuntament era que no calia tenir un pc a "l'ultima" i, per tant, sortir-los mes barat. Tambe, ara que hi penso, el que tu em proposes ja no es precisament un ordinador a "l'ultima" :-) Possiblement es poden trobar baratets. Ho proposare.

Com diu en SiscoGarcia no es necessita gaire màquina i realment es poden trobar grans gangues. A l'escola on vaig (no diré quina, no vull fer publicitat :lolflag: ) tenen ordinadors HP de sobretaula (dels que són plans, no de torre) amb 1Gb de RAM, 80Gb de disc dur i una gràfica Intel de 128Mb que com que té drivers lliures, no porta cap problema. Buscant, vaig trobar que en venien de segona ma per uns 90-100 euros i els venien en quantitats industrials. Trobo que una opció així seria bona si el que preteneu és estalviar.

---

### Post by Lotiopep on 2009-11-05
Moltes gracies a tots. Tindre en compte els vostres sugeriments.

---

