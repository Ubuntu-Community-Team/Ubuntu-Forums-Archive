---
title: "Connectar automàticament la wifi a l'iniciar el sistema"
date: 2011-12-25
forum: Catalan Team
---

### Post by Carles_BE on 2011-12-25
Hola a tothom

Tinc un portàtil GigaByte T1028G amb la pantalla trencada.
Per tal d'aprofitar-lo, he decidit fer una mica de bricolatge i fer-lo servir amb una pantalla externa, un teclat extern, un ratolí, etc ... la crisi, ja se sap

He instal·lat Lucid Lynx (perquè és la distribució que faig anar en altres màquines i la tinc una mica per mà) i tot va bé a excepció d'un tema que, o bé el soluciono o bé ja puc descartar la idea d'aprofitar el portàtil.

Resulta que, quan inicio el sistema la wifi sempre apareix desconnectada i he d'activar-la manualment pitjant les tecles Fn+F2 del teclat original del portàtil (que en aquesta màquina vénen marcades per a ficar en marxa o apagar la wifi). En canvi, amb el teclat USB que tinc connectat al portàtil aquesta seqüència de tecles no funciona.
Si el portàtil estés intacte cap problema ... però tal i com us he comentat la pantalla està trencada (i desmuntada) i, per a aprofitar-lo el muntaré d'una forma que no em permetrà accedir al teclat original.

RESUMINT:
**Necessito que la wifi s'activi automàticament quan faig login al sistema.**

Fins ara he provat instal·lant Wicd, però el "problema" persisteix. 
També he mirat d'aconseguir la versió Linux d'un programa de Gigabyte anomenat Smart Manager que et permet (en Windows) activar i desactivar wifi, bluetooth, 3G, baixar intensitat de pantalla, i en general totes les coses que poden fer-se amb la combinació de tecles FN+la-tecla-de-funció-corresponent ... però no l'he trobat pas.
He mirat pel google a veure si podia assignar funcions a les tecles però el que he vist supera els meus escassíssims coneixements ... i tampoc sé segur si és el bon camí

En fi, si algú em pot ajudar li estaré molt agraït

Cordialment

---

### Post by wgarcia on 2011-12-26
Potser hi hagi alguna opció a la configuració del BIOS que permeti això. Em refereixo al programeta de configuració general que s'obre en iniciar l'ordinador si prems F2 o F4 o alguna altra tecla, depèn de l'ordinador.

---

### Post by Carles_BE on 2011-12-26
Hola i gràcies per respondre tan aviat.

Ja vaig mirar això de la BIOS i hi ha una referència al teclat però només et permet triar la configuració del teclat entre diferents idiomes (alemany, coreà, xinès i algun altre que ni tan sols és l'anglès) ...

o sigui que sembla que per aquí no trobaré la solució

cordialment

---

### Post by kimet on 2011-12-26
Per fer-ho manualment has d'editar el fitxer /etc/network/interfaces (com a root) mira que hi digui entre d'altres:

#primari network interface
allow-hotplug eth0
iface eth0 inet dhcp

Hon canvies eth0 per la teva xarxa wifi, normalment wlan0, ho pots esbrinar amb ifconfig -a

Salut

Pd. Si tens instal.lat wicd es posible que et canvÏi aquesta configuració.
Prova-ho si fos el cas torna a preguntar.

---

### Post by CarlesOriol on 2011-12-26
Has mirat si hi ha cap actualització de la bios?

---

### Post by Carles_BE on 2011-12-27
Hola

abans de res gràcies per l'ajuda que m'heu donat ... 

En segon lloc, dono per SOLVED el tema. No me n'acabo de sortir però no vull invertir-hi més temps ... he parlat amb un amic i farem un canvi ... ell farà anar aquest portàtil amb W7 i me'n donarà un altre que sí que va amb Ubuntu ... i tots contents.

Moltes gràcies un cop més

Cordialment

---

### Post by papapep on 2011-12-30
Hola, Carles.

No es pot donar per resolt un tema quan, a la pràctica, no ho està,  o estem enganyant a qui llegeixi el títol i entri pensant que trobarà una solució al mateix. He modificat el fil conseqüentment.

Salut.

---

