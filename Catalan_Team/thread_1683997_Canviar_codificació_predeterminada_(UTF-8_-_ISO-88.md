---
title: "Canviar codificació predeterminada (UTF-8 - ISO-8859-1)"
date: 2011-02-08
forum: Catalan Team
---

### Post by xavi_xcs on 2011-02-08
Bona tarda,

estic instal·lant Festival i em surt un error i m'agradaria comprovar que no és degut a la codificació predeterminada que tinc (UTF-8 ), per això pregunto si algú sap com canviar (ja sigui a través del terminal o per alguna opció del menú) de UTF-8 a ISO-8859-1. 

Gràcies!

Salutacions!!

---

### Post by kimet on 2011-02-08
```
sudo dpkg-reconfigure locales
```

---

### Post by xavi_xcs on 2011-02-08
Primer de tot, gràcies per contestar.
Amb això no em deixa escollir quin vull, si ISO-8859-1 o UTF-8, el que simplement fa es reconfigurar-ho amb UTF-8:
ca_AD.UTF-8... up-to-date
...
Generation complete!

Només em fa això!

---

### Post by wgarcia on 2011-02-09
Si sols vols canviar un fitxer (o un conjunt de fitxers) de codificació, des d'una terminal es pot fer:

```

iconv --from-code=UTF-8 --to-code=ISO-8859-1  < fitxer > fitxer.temp
mv fitxer.temp fitxer

```

Si et diu que no troba iconv s'haurà d'instal·lar abans:
```

sudo apt-get install iconv

```

---

