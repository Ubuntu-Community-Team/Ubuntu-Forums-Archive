---
title: "Saber DNS a la que estic connectat"
date: 2012-06-08
forum: Catalan Team
---

### Post by akyra on 2012-06-08
Hola,

Des de la nova instal·lació de la versió 12.04, tinc algun problema amb la conexió VPN de la feina, bàsicament no resol la DNS.

Hi ha algun comando que em pugui dir les DNS que estic connectat, tipus ipconfig de windows?

Sí, ja sé que es pot mirar el fitxer "resolv.conf" però amb la nova versió fa referencia a un altre fitxer.

Gracies

---

### Post by wgarcia on 2012-06-09
Al gestor de conexions de xarxa (Network-manager), la icona del plafó superior, hi ha una opció que és "Informació de la connexió" i aquí surt tota la informació de la connexió. 

Des de la línia de comandes:

```
route -n
```

dóna també aquesta informació.

Si estàs darrera un router et donarà l'adreça del router, si vols veure a quines adreces apunta el router pots instal·lar "traceroute", i apuntant a qualsevol adreça et mostrarà com va resolent el nom:

```
traceroute ubuntu.cat
```

per exemple.

---

### Post by akyra on 2012-06-11
Moltes gracies, ho provaré.

---

