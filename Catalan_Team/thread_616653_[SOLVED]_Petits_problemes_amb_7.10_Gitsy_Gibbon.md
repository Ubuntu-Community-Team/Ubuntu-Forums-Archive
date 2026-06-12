---
title: "[SOLVED] Petits problemes amb 7.10 Gitsy Gibbon"
date: 2007-11-18
forum: Catalan Team
---

### Post by Curial on 2007-11-18
Bon hora baixa a tots!

Bé, com a comentari inicial diré que fins ara amb la versió 7.04 Fiesty Fawn no vaig tenir ni el més mínim problema des de l'inici. Ni un!! Si de cas alguna volta el problema era jo.

Dies després de passar a Gutsy Gibbon he viscut algun "penjament" de l'openoffice a l'hora d'imprimir tant amb el cups/pdf com amb la impressora.

Com que quan obria l'aplicació d'edició de dibuixos es penjava directament (o intentava recuperar un soposat document que mai ha existit, i es tancava), vaig decidir desinstal·lar des del synaptic tot el paquet d'openoffice.

Els "penjaments" els vaig solucionar, no però el tema d'impressora, així que vaig també eliminar-la des de sistema-administració-impressió i la vaig tornar a crear, Tot i això no m'imprimeix. També haig de dir que no m'imprimeix amb cap aplicació.(És una hp710c i des del guín-d'ous funciona perfectament)

Que m'aconselleu en un cas com aquest?

---

### Post by eduardsola on 2007-11-18
Pff... jo no t'aconsello res, sóc força inexpert i només et puc contar la meva experiència.

Jo tinc una HP Deskjet 5940 i des del dia que la vaig connectar me la va reconèixer sense cap mena de rencor, i funciona perfectament, però em passa el mateix que a tu, quan ha d'imprimir algun document gran, com un manual llarg, es penjen alguns programes. Amb l'aMSN m'ha passat.

Espero que algun usuari et tregui alguna solució ;)

---

### Post by papapep on 2007-11-19
Aquesta impressora t'ha de funcionar perfectament sota Linux:

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C)

En tot cas, cal que obris un fil específic per a cada problema que vulguis resoldre, amb un títol descriptiu, i que expliquis fil per randa què has fet i quins problemes concrets t'has trobat.

No estaria de més que fessis una llegida al fil de la capçalera on expliquem com cal plantejar els temes per a poder-ne aprendre tots plegats una mica:

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

---

### Post by Curial on 2007-11-19
> **papapep said:**
> Aquesta impressora t'ha de funcionar perfectament sota Linux:

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C)

En tot cas, cal que obris un fil específic per a cada problema que vulguis resoldre, amb un títol descriptiu, i que expliquis fil per randa què has fet i quins problemes concrets t'has trobat.

No estaria de més que fessis una llegida al fil de la capçalera on expliquem com cal plantejar els temes per a poder-ne aprendre tots plegats una mica:

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

Gràcies.Prenc nota.

---

### Post by Curial on 2007-11-19
> **eduardsola said:**
> Pff... jo no t'aconsello res, sóc força inexpert i només et puc contar la meva experiència.

Jo tinc una HP Deskjet 5940 i des del dia que la vaig connectar me la va reconèixer sense cap mena de rencor, i funciona perfectament, però em passa el mateix que a tu, quan ha d'imprimir algun document gran, com un manual llarg, es penjen alguns programes. Amb l'aMSN m'ha passat.

Espero que algun usuari et tregui alguna solució ;)

Gràcies Eduard, no es tractava però, de documents grans. M'ho fa amb tots, grans i petits. Aparentment tot està bé, els documents resten pendents a la finestra de documents encuats m'apareixen com a aturats i només em dona la opció de cancel·lar.

Aquest comportament me l'he trobat després d'actualitzar a la 7.10.

:) Salut

---

### Post by Curial on 2007-11-19
> **papapep said:**
> Aquesta impressora t'ha de funcionar perfectament sota Linux:

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C)

En tot cas, cal que obris un fil específic per a cada problema que vulguis resoldre, amb un títol descriptiu, i que expliquis fil per randa què has fet i quins problemes concrets t'has trobat.

No estaria de més que fessis una llegida al fil de la capçalera on expliquem com cal plantejar els temes per a poder-ne aprendre tots plegats una mica:

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

Gràcies Papapep, He fet tal com diu aquest enllaç que m'has donat i ara ja funciona perfectament: Només ha calgut fer [COLOR="Red"]sudo aa-complain cupsd[/COLOR] des del terminal.:popcorn:

---

