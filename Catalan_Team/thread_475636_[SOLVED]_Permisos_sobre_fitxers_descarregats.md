---
title: "[SOLVED] Permisos sobre fitxers descarregats"
date: 2007-06-16
forum: Catalan Team
---

### Post by TotAmbA on 2007-06-16
Bones de nou,
Tinc un petit problema sobre els fitxers que em descarrego amb l'Amule.
A l'ubuntu hi tinc una carpeta (compartit) que em serveix per intercanviar fitxers entre el linux i les altres màquines (windows). Si em descarrego qualsevol fitxer mitjançant el navegador i el poso en aquesta carpeta compartida, puc estirar aquest fitxer desde windows sense problemes. A l'inversa (desde windows cap a linux) també em funciona perfectament. Si hi poso un document de word o de openOffice, també el puc moure, modificar, executar.

El problema està en els fitxers que es descarreguen de l'amule no són accessibles. He de modificar les propietats de cada fitxer (donar permisos de lectura i escriptura) que es descarrega.  Això ho faig per poder accedir desde els sistemes operatius windows. Sincerament, no se dir-vos si desde linux els puc executar.

Si intento modificar els permisos de la carpeta "compartit" no m'aplica els canvis. Hi poso a "accés al fitxer" "lectura i escriptura", aplico, i no em modifica els canvis. He intentat fer el mateix en altres carpetes dins de "compartit" i em passa el mateix. Per modificar els permisos dels fitxers no tinc cap mena de problema.

La carpeta "compartit" la vaig crear de la següent manera:
Entrant amb el meu unic usuari, vaig crear la carpeta "compartit", botó dret, comparteix carpeta. Em surt una finestra on posa el camí de la carpeta,  comparteix per: "Xarxes windows (SMB)", nom i descripció del recurs compartit. També hi tinc deshabilitat "només lectura".

Cal dir que he intentat modificar els permisos d'aquesta carpeta amb un "sudo nautilus" i em passa el mateix problema.
El propietari d'aquesta carpeta és el meu usuari, no pas el root.

No se si m'he explicat bé, i si he donat la suficient informació.
Alguna idea?

Gràcies.

---

### Post by TotAmbA on 2007-06-17
Fent proves he detectat que amb un sudo nautilus o nautilus  no se'm modifiquen els permisos sobre carpetes. Sobre els fitxers si que puc fer modificacions de permisos.

---

### Post by AlexMuntada on 2007-06-17
Voleu dir que no és l'amule el que els canvia?  Sembla com si estés a l'aguait i els canvies en pic ho feu vós per assegurar que no tingueu cap problema de seguretat, potser.

En tot cas, podríeu assegurar-vos que sou el propietari dels directoris comprovant que no surten en el llistat que resulta d'executar això: ```
find ~ ! -user $(whoami)
```

---

### Post by TotAmbA on 2007-06-20
Gràcies Lluis, com tu també havies comentat el problema no és sobre els permisos d'ubuntu. El problema estava en l'Amule. Quan s'acabava de descarregar un arxiu, el desava amb uns permisos (predeterminats per amule) que no permetia accedir a ells desde els altres equips. Per canviar els permisos predeterminats anem a Amule, preferències, seguretat, "**permisos predeterminats"** i modifiquem a 777 (o el que us convingui) tant fitxers com carpetes.

Salutacions i gràcies de nou per l'ajuda rebuda.

---

### Post by AlexMuntada on 2007-06-20
No sé pas d'on heu tret que em dic Lluís... :p

En qualsevol cas, no acostuma a ser una bona idea en termes de seguretat tenir permisos 777.  Aneu amb molt de compte!

---

