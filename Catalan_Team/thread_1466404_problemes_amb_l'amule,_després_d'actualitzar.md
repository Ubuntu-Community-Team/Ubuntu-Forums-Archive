---
title: "problemes amb l'amule, després d'actualitzar"
date: 2010-04-30
forum: Catalan Team
---

### Post by marmotona on 2010-04-30
Quan he acabat de fer l'actualització, he intentat reactivar els repositoris de tercers i m'ha dit que el de la SVN de l'amule era obsolet. Així es que l'he esborrat, però no em deixa obrir l'amule ni tornar-lo a instal·lar ni instal·lar cap altre programa p2p.

En el terminal, quan vull engegar l'amule, em diu:

> $ amule
amule: error while loading shared libraries: libbfd-2.20.so:  cannot open shared object file: No such file or directory

Què creieu que podria fer?.

---

### Post by wgarcia on 2010-04-30
Segons el que tens a la terminal sembla que sí que el tens instal·lat, però no troba una llibreria que necessita. 

Entrant el nom d'aquesta llibreria a google, m'ha sortit una solució, que és entrar a una terminal el següent:

sudo ln -s /usr/lib/libbfd-2.20.1-system.20100303.so /usr/lib/libbfd-2.20.so

Et demanarà la clau. Això el que fa és crear un "enllaç simbòlic" per a la llibreria que no troba. Mira si això ho soluciona.

---

### Post by marmotona on 2010-04-30
> **wgarcia said:**
> Segons el que tens a la terminal sembla que sí que el tens instal·lat, però no troba una llibreria que necessita. 

Entrant el nom d'aquesta llibreria a google, m'ha sortit una solució, que és entrar a una terminal el següent:

sudo ln -s /usr/lib/libbfd-2.20.1-system.20100303.so /usr/lib/libbfd-2.20.so

Et demanarà la clau. Això el que fa és crear un "enllaç simbòlic" per a la llibreria que no troba. Mira si això ho soluciona.

Sí, sí, me l'ha deixat iniciar des de terminal. Gràcies.

---

