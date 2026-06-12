---
title: "[RESOLT] No puc instalar ni l' ubuntu ni el kubuntu"
date: 2007-05-12
forum: Catalan Team
---

### Post by ilion1250 on 2007-05-12
* El kubuntu no em passa de la segona pantalla, després de l' intro  es queda pensant i pensant (amb la barra blava movent-se) i haig d' apagar l' ordinador.
* Amb l' ubunto quasi arrivo al final, estant el procés d' instal.lació al 97% es queda clavat configurant un dispositiu de magatzemament USB que jo no tinc. No m' ha quedat altra opció de sortir de la instal.lació.
També ho he intentat amb el fedora i el debian he arrivat fins al final pero després cap dels dos programes se m' ha carregat quan comença sembla que va bé pero s' atura, en el cas del debian l' ultima línia d´informació que diu:
**ACPI: PCI Interrumpt 0000:00:02.6[c]-> GSI 18 (level, low) -> IRQ 169**
En el cas del fedora s' atura amb el missatge:
[B]S' està iniciant el udev:
[/B]
Algú em pot donar una mà, em temo que el problema sigui el meu ordinador, es un packard bell, 521MB, pentium 4, 2.50 Ghz peró potser porta quelqom de fàbrica que m' està impedint instal.lar qualsevol linux.

---

### Post by lluisanunez on 2007-05-12
I et funciona en Live CD?

Si pots entrar la comanda ```
linux acpi=off
``` un cop hagis carregat el CD, em sembla que això arrenca l'instal·lador sense ACPI

---

### Post by ilion1250 on 2007-05-13
El live cd de l ' ubuntu em funciona be, el del kubuntu és el que es queda clavat.
Probaré el que em dius, suposo que haig de posar la instrucció que m' has indicat a la primera pantalla abans de prèmer intro.

---

### Post by patrickfromspain on 2007-05-13
Podries probar tambe amb irqpoll

---

### Post by ilion1250 on 2007-05-19
Fa uns dies vaig fer una consulta, no hi havia forma de instal.lar cap distribució, ni l' ubuntu, ni el fedora, debian etc.
Em veu aconsellar instal.lar sense l' ACPI o veure l' irqpoll.
Finalment quasi desesperat he descobert quin era el problema i ho comunico a la comunitat per si es d' utilitat.
El problema era **el bluetooth**, m' explico, tinc una pda que sincronitzo via windows XP amb l' activesync, per no connectar el cable usb  cada vegada vaig comprar un bluetooth que s' instal.la a un port lliure usb, la marca es belkin. Doncs bé, quasi desesperat i a punt d' abandonar se'm ha ocorregut treure aquest dispositiu i ¡aleluia¡, a la primera m' ha entrat el debian 4.0.

---

### Post by papapep on 2007-05-20
Això hauries de posar-ho a la consulta que vas fer a fi de qui tingui un problema similar trobi el principi i el final del tema. No cal obrir un fil nou per a la solució.

Salutacions.

---

### Post by orestesmas on 2007-05-21
Ah! aleshores potser el què passava és que el PC intentava arrencar d'aquest dispositiu USB, i no podia perquè no tenia cap disc bluetooth accessible.

Segurament el problema el pots solucionar entrant a la BIOS i canviant la seqüència de dispositius d'arrencada, però si traient-lo et va bé, doncs ja està.

---

