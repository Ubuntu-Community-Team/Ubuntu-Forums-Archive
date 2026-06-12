---
title: "Client Linux servidor AD w2k3"
date: 2007-09-19
forum: Catalan Team
---

### Post by hakd0c on 2007-09-19
M'intentare explicar.

A l'oficina tenim un Active Directory (AD) muntat en un Windows 2k3 server. Jo soc el primer que treballa amb Gnu/Linux, en aquest cas Ubuntu Feisty.

La qüestió es que seguint aquesta guia [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) i alguna altre que he anat trobant, ja tinc l'autenticació del meu usuari a l'AD (ja no es un usuari local).

Fins aquí cap problema, el problema be amb què m'he quedat sense so, tampoc puc muntar unitats i molt menys encara que s'automontin les unitats extraibles.

He provat amb:

-Crear grups amb el mateix nom que al sistema local i incloure-hi el meu usuari, però com que el gid es diferent no serveix de res.

-He creat un grup a l'AD de nom linux, m'hi he posat i he editat el fitxer /etc/group per posar a tots els grups on hi havia l'usuari creat a la instal·lació el grup linux, però al fitxer /etc/group no si pot posar com a usuari un grup i per tant tampoc funciona.

Se que una possible solució es editar el fitxer /etc/group i posar el meu nom d'usuari de l'AD a tots els grups de l'usuari de la instal·lació i això solventaria el meu cas.

Però si es tractes d'una xarxa amb 20 o 30 usuaris i 20 o 30 maquines on els usuaris no tinguessin maquina assignada (tipus cibercafe o telecentre ...) aquest sistema seria impracticable.

Hi ha alguna manera pràctica de poder fer que els usuaris d'un AD tinguin privilègis d'escriptori? (So, automuntatge de medis extraibles ...)

---

### Post by pespin on 2007-09-19
Jo diria que des del menú Sistema->Administració->Usuaris i Grups tens algunes de les opcions que busques per a posar-li a l'usuari.

---

### Post by hakd0c on 2007-09-19
Hola Pespin

> **pespin said:**
> Jo diria que des del menú Sistema->Administració->Usuaris i Grups tens algunes de les opcions que busques per a posar-li a l'usuari.

El meu usuari no es un usuari del sistema local, per tant no surt a la llista a part que el què m'interessaria i potser he expressat malament, es no haver d'anar modificant la configuració màquina a màquina, sinó que per defecte els usuaris de l'AD tinguessin el so i automontatge d'unitats.

---

