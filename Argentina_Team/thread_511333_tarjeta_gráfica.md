---
title: "tarjeta gráfica"
date: 2007-07-27
forum: Argentina Team
---

### Post by marcesneibrun on 2007-07-27
ante todo quiero agradecer a todos los q ayudan a gente como yo q recien comienzo a moverme en el mundo linux y en especial ubuntu.......
Mi duda es la siguiente, donde me fijo en la compu q tarjeta grafica tiene mi compu??( Nvidia o Ati)
Gracias ,
Marcelo

---

### Post by beuno on 2007-07-27
Sistema > Preferencias > Informacion de Hardware

---

### Post by jajajavi on 2007-07-27
también podés poner en la consola
```
lspci
```  
y te tira entre otras cosas un **VGA compatible controller**

---

### Post by jpmorelli on 2007-07-28
O también como leí en la web de Cesarius

sudo lshw

y para tenerlo en un archivo tipo html para leerlo mejor

sudo lshw -html > nombre_de_archivo.html

Tira excelente info sobre todo el sistema !!!

---

