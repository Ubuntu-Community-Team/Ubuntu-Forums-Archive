---
title: "passar a Feisty"
date: 2007-04-29
forum: Catalan Team
---

### Post by montse on 2007-04-29
Hola,

vull passar l'Ubuntu del 6 al 7. A [www.ubuntu.com/getubuntu/upgrading](www.ubuntu.com/getubuntu/upgrading) diu que cal tenir instalada la versió 0.45.2 de l'update-manager, i em dóna més informació a wiki.ubuntu.com/EdgyUpdatesEnabled.
A mi el Synaptic em diu que l'última disponible és la 0.42.2ubuntu22. Intento fer el que m'indica aquest wiki que deia:

open Settings/Repositories and make sure that the "Internet Updates/Recommended updates" checkbox is checked. After a reload the update package will be available.

i em trobo que al meu Synaptic (en català), a la pestanya "Actualitzacions d'internet" no hi ha cap checkbox que digui res semblant a "Actualitzacions recomanades". El que tinc marcat és que comprovi les actualitzacions diàriament.

Què passa?

D'algun dels missatges d'aquest fòrum havia copiat aquest mètode per pujar de versió:

Editar el sources.list (sudo gedit /etc/apt/sources.list) i substituir les entrades edgy per feisty i guardar.
sudo apt-get update
sudo apt-get dist-upgrade
reiniciar0

però em pregunto: funcionaria sense tenir la versió 0.45.2 de l'update-manager? No m'atreveixo a provar-ho...

---

### Post by patrickfromspain on 2007-04-29
jo diria que ha de funcionar.. de totes formes, jo prefereixo una instal·lacio de 0... y encara mes si tens coses instalades de repositoris no oficiales o compilades de 0.

salut!

---

### Post by CarlesOriol on 2007-04-29
si fas això a ma...

asegurat que el darrer sudo apt-get dist-upgrade hagi finalitzat correctament i si no és així repeteix-lo tants cops com calgui.

Però millor consulta: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by montse on 2007-05-02
Sï sí, això és el primer que vaig consultar, d'aquí venia el dubte que plantejo i que segueix obert...

Reinstalar en lloc de "upgrade" (com es diu això en català?) no em convenç perquè m'imagino que hauria de refer moltes coses que ja tinc fetes (configuracions de programes, d'accés a internet, etc.). És així, oi?

---

### Post by papapep on 2007-05-02
Evidentment reinstal·lar implica haver de posar totes les aplicacions que no s'instal·len per defecte. El que et convé més (excepte que tinguis uns requeriments molt especials) és actualitzar (així es diu "upgrade" en català). 
Amb un simple "sudo aptitude dist-upgrade" (després d'haver fet un "sudo aptitude update") tot hauria de rutllar decentment.
Pensa que, en el fons, tots els programes fan servir el mateix programa "de fons", amb el qual si has de tenir problemes els tindràs igual amb Synaptic que amb aptitude o amb apt-get.

Però per les experiències que estem veient, no és probable que tinguis massa complicacions.

Salutacions i sort.

---

### Post by PellRoja on 2007-05-02
pel que veig tens la edgy. per ejecutar el update-manager i canviar de versió has de 

gksudo "update-manager" -c

fa que si hi ha una nova versió puguis actualitzar. :P

---

### Post by montse on 2007-05-03
bones,

he fet això últim i resultal qeu l'opció -c no existeix. Mirant el man he deduït qeu la correcta potser seria -k. Ho he fet, m'ha instal·lat un parell d'acutalitzacions de llibreries, però la versió de l'update-manager segueix sent la 0.42.2ubuntu22, i el Synaptic segueix dient que aquesta és l'última disponible. Però al web d'upgrade d'Ubuntu diu que

The latest version of Update Manager (0.45.2) must be installed before you upgrade.

Per això segueixo sense atrevr-me a fer el sudo aptitude dist-upgrade (després d'haver fet un "sudo aptitude update") que m'indica el papapep!

---

### Post by papapep on 2007-05-03
Si vas al [lloc web dels paquets de l'Ubuntu]("http://packages.ubuntu.com") i hi busques update-manager, veuràs que Update manager és només una interfície gràfica d'apt, amb el qual, et torno a insistir, et passarà de bó o dolent el mateix amb Update manager que amb aptitude o apt-get. **Estaràs executant el mateix programa** . (Sol haver-hi més problemes amb les interfícies que amb els programes de fons, són una capa més per acumular errors).
Fins i tot, si tens alguna inconsistència als paquets que provoqui que l'Update-manager no t'acabi d'anar a l'hora, actualitzant per consola té números de que s'arregli.

Salutacions.

---

### Post by montse on 2007-05-03
aaaaaaahhhhhhhhhhhh.....

va bé. Ja ho provaré. Doncs vaja, el web d'Ubuntu lia una mica, no?

Parlant d'actualitzacions, l'avisador aquest que cada dia et diu que hi ha actualitzacions per instal·lar no m'ha avisat ni de la nova versió d'Ubuntu ni de la d'OpenOffice. I el Synaptic diu que l'última disponible d'OpenOffice és la 2.0. Com és?

---

### Post by patrickfromspain on 2007-05-04
perque en una version que ja s'ha llançat, nomes hi ha actualitzacions de seguretat, no de versions.

---

### Post by CarlesOriol on 2007-05-04
Més concretament:

 Hi ha correcions no ampliacions.

---

