---
title: "Realment fa falta la swap?"
date: 2009-03-23
forum: Catalan Team
---

### Post by Daerun on 2009-03-23
La primera vegada que vaig instal·lar Ubuntu (la 7.10, just abans que arribés la 8.04), em van dir que havia de crear una partició swap d'uns 2 Gb; però realment serveix d'alguna cosa? Les vegades que he comprobat el seu funcionament a través del monitor del sistema, rarament superaba el 2% d'us, inclús tenint mitja dotzena de processos oberts...

---

### Post by papapep on 2009-03-23
Ras i curt i sense entrar en explicacions tècniques: sí. 

Si no la tens i tens problemes, la trobaràs a faltar ;)

---

### Post by Daerun on 2009-03-24
D'acord doncs :lol: Però, i entrant en explicaciones tècniques? M'has picat la curiositat.

---

### Post by kukat on 2009-03-24
Si, sobretot als equips antics diria jo. 

En els PC d'aquí de classe, que tenen 500 MB de RAM, si no tenen la memòria SWAP van molt malament. 

Ho dic per experiència, Vaig tindre que configurar l'arxiu /etc/fstab per a afegir-li la partició SWAP, i va ser quan va començar a funcionar a un rendiment òptim! jejej (anaven molt lents i es penjaven de qualsevol cosa,,,)
;)

---

### Post by thedavis on 2009-03-24
La swap es com la memoria virtual als Windows, sense aquesta partició el sistema no pot paginar els procesos de memoria al disc i es "colapsa". 

Generalment s'ha de tenir el doble de swap que de RAM, això quan tenim menys de 1GB de RAM. Si tenim 1GB cal configurar 1GB de swap. A partir de 2GB cap amunt, es recomenable, no superar els 2GB de swap. 

Amb la comanda "free" podem veure l'ús actual de la memoria virtual, per molt poc que es faci servir, a la swap, sempre tindrem dades.

Jo amb 4GB de RAM i 2 de SWAP, la sortida de free:

```
                       total       used       free     shared    buffers     cached
Mem:                  4046032    3741636     304396          0      21924    1798168
-/+ buffers/cache:    1921544    2124488
Swap:                 1951888       5532    1946356
```

---

### Post by kukat on 2009-03-25
:confused:

Jo tinc 2Gb de RAM i 4 de SWAP.....deuria de posar-li menys SWAP?

---

### Post by thedavis on 2009-03-25
Pots deixar-ho tal com està, pero segurament mai facis servir els 4GB de swap al 100%, jo amb els 2GB mai he pasat del 22%...amb 2 windows xp funcionant (vmware server) al mateix temps...

---

