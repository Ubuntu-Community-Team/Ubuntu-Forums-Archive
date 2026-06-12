---
title: "Automatix i error ara en l'ATP i Sinaptyc :-("
date: 2007-05-18
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-05-18
He estat intentat instal·lar el Vmware des de l'Automatix.. i nosé.. no trobava l'icona.. a part que m'ha fet una cosa que sembla que s'hagués quedat a la meitat. Doncs bé li he dit de desinstal·lar.

Doncs bé, ara tant l'ATP, com el Synaptyc, com l'Automatix quan vull instal·lar qualsevol progrma em diu això:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

:( Aii que he fotut una cagada de les grosses... que haig de fer?

---

### Post by patrickfromspain on 2007-05-18
**dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.**

;)

---

### Post by papapep on 2007-05-18
Jo sóc particularment escèptic amb aquestes eines super-automatitzades per instal·lar paquets.apt-get, aptitude i synaptic fan la seva feina de manera segura i correcta. Com has pogut comprovar tu mateix "a les teves carns", a vegades automatix i similars fan un desgavell a la base de dades de programari.

Per començar a intentar arreglar-ho, podries provar a executar la comanda que et dóna l'error:
```
sudo dpkg --configure -a
```

A veure que tal. (i evidentment, no tornaria a fer servir automatix)

---

### Post by bikerbaixcamp on 2007-05-18
> **papapep said:**
> Jo sóc particularment escèptic amb aquestes eines super-automatitzades per instal·lar paquets.apt-get, aptitude i synaptic fan la seva feina de manera segura i correcta. Com has pogut comprovar tu mateix "a les teves carns", a vegades automatix i similars fan un desgavell a la base de dades de programari.

Per començar a intentar arreglar-ho, podries provar a executar la comanda que et dóna l'error:
```
sudo dpkg --configure -a
```

A veure que tal. (i evidentment, no tornaria a fer servir automatix)

Fent això que m'has dit, s'ha solucionat. Gràcies.

Doncs es que estava buscant això del VMware i resulta que al APT també hi és. Però bé, alguna cosa (cada cop menys ) no hi és; i es troba fàcilment a l'Automatix. De totes maneres, sempre l'intento evitar ja que no és una cosa oficial.

Estic cercant una màquina virtual, i VirtualBox va bé, però no sé com va el tema de l'USB (obriré un post) i ara amb el VMware a l'obrir-lo em demana buscar un arxiu amb el format .vmx No sé.. 

:KS

---

### Post by papapep on 2007-05-19
Doncs t'està demanant pròpiament la màquina virtual. L'Vmware només les executa.
A la plana [http://www.easyvmx.com](http://www.easyvmx.com) podràs crear màquines virtuals fàcilment i ràpidament.

Salutacions.

---

