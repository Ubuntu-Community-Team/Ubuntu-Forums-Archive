---
title: "No puc fer CHMODª"
date: 2010-11-10
forum: Catalan Team
---

### Post by tanreb20 on 2010-11-10
Hola!

Avui m'he baixat un script i volia donar.li permisos d'execurció.

He provat de fer el tipic

```
chmod +x script.sh
```

pero em temo que no funciona :'( Ho he provat amb root i tampoc, els permisos de l'arxiu són:

```
rw- r-- r--
```

Algú sap com recuperar el chmod?

---

### Post by wgarcia on 2010-11-10
Et falta el bit que diu a qui li estàs donant permisos,

a: tots
o: el grup
u: l'usuari

Per exemple per donar-li permís d'escriptura a l'usuari:

chmod u+w fitxer

Per donar-li permís d'execució

chmod u+x fitxer

---

### Post by tanreb20 on 2010-11-10
Uhmmm pensava que no calia posar-lo! Merci!

---

