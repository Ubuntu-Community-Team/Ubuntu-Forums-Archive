---
title: "error copiant arxius a la memòria flash"
date: 2017-11-17
forum: Catalan Team
---

### Post by josep-maria on 2017-11-17
El backup sempre havia anat bé fins avui. Quan faig copio tots els arxius a un llapis de memòria, em dóna error a dues de les carpetes de fotos, sempre les mateixes. Que fa molt de temps que no he tocat. Diu: hi ha hagut un error creant la carpeta "fotos", error d'entrada/sortida. També em dóna un error per cadascuna de les fotos.

He mirat a: propietats > permisos > accés a la carpeta, i diu "crear i suprimir". A "accés al fitxer" hi ha uns guionets (---). Si hi poso "lectura i escriptura", i faig clic a "aplica els permisos", ho esborra i hi torna a posar els guionets. Les altres carpetes tenen els mateixos permisos, amb els guionets, i funcionen bé. He provat amb un altre pen, i tampoc no puc gravar-hi les dues mateixes carpetes.

---

### Post by josep-maria on 2017-11-17
Tinc l'Ubuntu Mate 1.12.1, release 16.04.3, Linux 4.4.0-98-generic i686, processador Celeron G1620

---

### Post by wgarcia on 2017-11-18
Suposo que en el Mate el gestor de fitxers és "Caja". Potser reiniciar Caja pot arreglar el problema. Aturant-lo :

```
killall caja
```

i obrint qualsevol carpeta, suposo es reiniciarà. 

Si fas servir Nautilus a més s'ha d'esborrar un fitxer de configuració, però no sé si serà el cas.

---

### Post by josep-maria on 2017-11-18
Ja va bé. Moltes gràcies.

---

