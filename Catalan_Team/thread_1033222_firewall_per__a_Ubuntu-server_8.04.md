---
title: "firewall per  a Ubuntu-server 8.04"
date: 2009-01-07
forum: Catalan Team
---

### Post by carlesbm on 2009-01-07
Hola 

   Unaltre cop per qui fent preguntes.

   M'he instalat un servidor a casa amb Ubuntu server 8.04 i estat pensant que hem falta un tallafocs per evitar que algu pugui accedir al servidor amb males intecions.


  He buscat per la net i he vist que hi ha força recursos però no se pas quin escollir, un que he vist que la gent diu que es mot comode de configurar es el Shorewall, que mes que res ens permet de configurar el Iptables de una forma més amena i simple.


   Que hem podeu aconsellar per tal de protegir el servidor?


  Moltes gracies

:):)

---

### Post by papapep on 2009-01-07
Ubuntu fa servir com a interfície a iptables (que és el que són tots aquests programes, no et pensis que cap d'elles fa servir res més. Només són màscares a l'iptables) un que s'anomena UFW (Uncomplicated FireWall). A partir de la 8.10, l'UFW té una interfície gràfica (gufw), per a poder gestionar les regles d'accés, abans (de la 8.10) és una eina d'intèrpret d'ordres.

---

