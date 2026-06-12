---
title: "Tsclient vs Terminal Server original"
date: 2010-11-18
forum: Catalan Team
---

### Post by Contaboy on 2010-11-18
Bon dia,

Abans utilitzava WXP. Ara m'he passat a Ubuntu 10.10

Només tinc un problema.

Puntualment he de fer connexions a un servidor de la meva empresa. Abans executava a la consola de WXP o W7 l'ordre mstsc /admin i obria una connexió de Terminal Server interactuant amb la sessió oberta (sempre que coincidís el login).

Quan utilitzo Tsclient (que ve incorporat a Ubuntu) em trobo que puc connectar ja que simula la Terminal Server de Windows però m'obre una nova sessió i jo el que vull es que m'interactui amb la sessió que ja és oberta,

Alguna idea ? Possiblement tingui que fer com a XP i executar alguna cosa a la terminal

---

### Post by Contaboy on 2010-11-18
EM responc a mi mateix:

rdesktop -0 [ip maquina remota]

---

### Post by wgarcia on 2010-11-18
Contaboy, posa-li si pots "Solved" (Thread tools -> Solved) al fil així queda constància que hi ha una solució en ell a aquest problema.

---

