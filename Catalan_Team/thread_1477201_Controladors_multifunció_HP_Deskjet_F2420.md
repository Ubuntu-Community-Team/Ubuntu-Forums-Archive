---
title: "Controladors multifunció HP Deskjet F2420"
date: 2010-05-07
forum: Catalan Team
---

### Post by BoitanO on 2010-05-07
Aquest fil va començar, amb un altre tema, aquí: [http://ubuntuforums.org/showthread.php?p=9262661](http://ubuntuforums.org/showthread.php?p=9262661)

Bé, gràcies per tot, al final, despres de la temporada fora de casa i els meus pares patint davant de llauna aquella per veure si imprima, al final han desistit i han decidir comprar una nova impresora, en aquest cas una HP, crec que una 2420. 

Tinc entès que és bastant mes compatible amb linux que les lexmark, no?

Salut a tothom!

---

### Post by papapep on 2010-05-07
Home, sí, però seria bastant més pràctic (i econòmic) i segur si mires/preguntes si el model/marca és compatible abans de comprar, no després :)

Si hem de fer cas a la "biblia" de les impressores en Gnu/Linux ([http://www.openprinting.org](http://www.openprinting.org)), el model que esmentes (és una Laserjet?):

[http://www.openprinting.org/printer/HP/HP-LaserJet_2420](http://www.openprinting.org/printer/HP/HP-LaserJet_2420)

funcionarà perfectament. Probablement només endollar-la la detecti i faci ell mateix (l'Ubuntu) el que calgui.

---

### Post by BoitanO on 2010-05-08
Doncs no, no és una laserjet... és una **deskjet**... i ara l'estic provant amb un xubuntu, i no aconsegueixo que m'escanegi... (tampoc ho he aconseguit amb "lo puto" Windows XP ](*,), *"Ai señor, llévame pronto"*)

M'he baixat el djtoolls, per veure si aconseguia algo de profit, però crec que només milora les opcions d'impresió, ja que no he trobat RES que em fes pensar que m'escanejaria alguna cosa, ja m'ha imprimit bé des de bon començament.

També he de dir que ho estic provant des d'un live CD...

Fins aqui tot, per ara...

Salut!

---

### Post by papapep on 2010-05-08
Bé, doncs podries començar instal·lant els paquets "normals" per la majoria de equips HP i per escanejar:

```
sudo aptitude install hplip hpijs xsane
```

Si ja els tens instal·lats no farà res, si no els tens farà el fet.

Atura l'impressora i l'ordinador, desendolla-la del port USB i tornar-ho a engegar tot. Un cop estigui l'ordinador engegat i amb la sessió d'usuari oberta, endolla la màquina al port USB (quan estigui engegada, clar). A veure si veus la llum.

EDICIÓ: aquí: [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2400_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2400_series.html) diu que ha d'anar ferpectament tot plegat amb el controlador hplip (que és un dels que et dic d'instal·lar).

---

### Post by papapep on 2010-05-08
Uhm, entono un "mea culpa" per no haver reaccionat abans. Una de les màximes del fòrum: "un tema, un fil". O sigui, que com que ara estem parlant d'un altre equip respecte el que va motivar la teva creació del fil, n'obro un altre i hi passo els apunts que parlen del F2420, per seguir-ne parlant si cal.

El nou fil és: [http://ubuntuforums.org/showthread.php?t=1477201](http://ubuntuforums.org/showthread.php?t=1477201)

---

