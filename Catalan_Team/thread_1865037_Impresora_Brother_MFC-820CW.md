---
title: "Impresora Brother MFC-820CW"
date: 2011-10-19
forum: Catalan Team
---

### Post by akyra on 2011-10-19
Hola he instal·lat aquesta impressora i tinc dos petits problemes, un que hem diu que la impressora no té tinta, o sigui que no llegeix els nivells de tinta, ja que sí que en té, ah, la impressora imprimeix.

L'altre és que per instal·lar els drivers d'aquesta impressora ho he hagut de fer mitjançant el comando: 
> dpkg -i --force-all --force-architecture mfc210clpr-1.0.2-1.i386.deb

és el paquet que he utilitzat per totes les versions i ha funcionat bé, però ara em surt un error que diu:
> E: The package mfc210clpr:i386 needs to be reinstalled, but I can't find an archive for it. Normalmente esto significa que ha instalado paquetes cuyas dependencias no se han podido satisfacer

Amb aquest segon error no em deixa fer servir synaptics ni el centre de software.
El synaptic em dóna el següent error:
> E: El paquete mfc210clpr:i386 necesita ser reinstalado, pero no se encuentra un archivo para éste.
E: Error interno al abrir el caché (1). Por favor informe de este error.


Gracies

Sabeu que es pot fer per treure aquest dos errors.

---

### Post by akyra on 2011-10-19
Bé he solucionat el problema del paquet fent això:
1.- He anat al directori "/var/lib/dpkg/info" com root i he buscat els arxius del mfc210 i els he esborrat.
Després he executat
> sudo dpkg --remove --force-remove-reinstreq mfc210clpr:i386

i ja m'ha deixa instal·lar coses.

Ara queda el tema de la tinta que mai m'havia sortit.

Salut

---

### Post by wgarcia on 2011-10-20
A mi també em surt amb el model Brother DCP-375CW. Deu ser un problema dels controladors d'aquestes impressores. Pel que he vist des que surt aquest missatge, és inofensiu. Sortosament desapareixerà en alguna actualització futura.

---

### Post by akyra on 2011-10-20
Quin dels dos errors, el de la tinta o el del paquet?

Si és el del paquet, no em deixava fer res amb el synaptic.

Adeu

---

### Post by wgarcia on 2011-10-20
No, vull dir el de la tinta, que a més el tinc en altres models d'impressora a la feina.

El del paquet sí que et pot generar problemes d'actuailtzació d'altres paquets.

---

### Post by akyra on 2011-10-21
Avui intentaré desintal·lar tot el que tinc de la impressora i tornar-ho a instal·lar de nou, ja que ara no em funciona.

Hi alguna manera de treure el control de nivell de tinta, si no val per res...

Adeu

---

