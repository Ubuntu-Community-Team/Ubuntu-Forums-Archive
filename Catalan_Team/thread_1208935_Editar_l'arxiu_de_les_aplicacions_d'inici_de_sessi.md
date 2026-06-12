---
title: "Editar l'arxiu de les aplicacions d'inici de sessió"
date: 2009-07-09
forum: Catalan Team
---

### Post by Turtun on 2009-07-09
Hola de nou,

Voldria editar i/o ordenar les aplicacions/comandaments que s'executen a l'inici de sessió per poder afegir-n'he un (desde l'entorn gràfic se com afegir/borrar-ne), perquè s'executi un cop tota la resta d'aplicacions s'hagin carregat, és a dir que s'executi l'últim. A més vull ordenar-ne 2 més que crec que em donen "problemes" perquè no s'executen en l'ordre correcte.
He estat buscant l'arxiu on crec que deu guardar aquest ordre de càrrega d'aplicacions però m'ha resultat impossible trobar-lo. Crec que abans, amb l'Ubuntu 7.10, tenies l'opció a l'afegir aplicacions en entorn gràfic de donar-li aquest ordre, però amb l'Ubuntu 8.10 no se pas com fer-ho.

Algú sap quin arxiu guarda aquesta configuració i si es pot canviar l'ordre en el que s'executen les aplicacions de l'inici?

Gràcies per l'ajud.

---

### Post by papapep on 2009-07-10
Quan dius "aplicacions" no sé si et refereixes a serveis o a programes que s'executen a nivell d'usuari.

En tot cas, el sistema de control de serveis, i la seva precedència i a quin [nivell d'execució]("http://es.wikipedia.org/wiki/Runlevel") s'executen, a l'arrencada es gestiona amb un sistema no especialment amigable (igual hi ha alguna interfície gràfica, però no la conec).

Si fas a un intérpret d'ordres:

```
man update-rc.d
```

et sortirà un munt d'informació al respecte (en anglès, clar)

---

### Post by Turtun on 2009-07-11
Gràcies per respondre Papapep,

De fet de moment només em refereixo al que pots trobar en "Sistema/Preferències/Sessions/Programes d'Inici", soc un usuari molt bàsic encara i no pico més lluny :P 
De fet si et soc sincer he executat l'ordre que m'has dit i m'ho he llegit tot a veure si aprenia quelcom nou però... no he entès pràcticament re malauradament ja que poder van per aquí els trets :sad:
La pàgina de Wikipèdia, també l'he llegit, però fa referència al carregador Gurb (no crec que vagi per aquí la solució), quan buscava googlejant trobava moltes referències al Gurb també, poder perquè no se expressar la pregunta clarament.

En resum, vull poder donar un "ordre" als "Programes d'inici" que hi ha a  "Preferències de les sessions"; per posar un exemple, que s'inicii primer el Gestor de Bluetooth i l'últim a iniciar que sigui l'Escriptor Remot.

Salutacions i gràcies de nou per l'ajud.

---

