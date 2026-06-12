---
title: "Busqueda de paquetes usando auto-apt"
date: 2006-11-26
forum: Argentina Team
---

### Post by QUASAR_FREAK on 2006-11-26
Cuantas veces nos paso que queríamos compilar algo y en el momento de tirar configure se quejaba que faltaba X archivo y debíamos buscar a que paquete pertenecía ese archivo por internet para luego instalarlo, bueno con esta utilidad safamos.

Primero instalemos el auto-apt
[LEFT]```
sudo apt-get install auto-apt
```[/LEFT]
 
Vemos las sintaxis de auto-apt:
auto-apt [opciones] comando [argumentos]

Para ver información sobre los argumentos ejecuten auto-apt

Volviendo al ejemplo de compilar, esta vez ejecutamos el configure usando auto-apt, así cuando configure se queje por la falta de X archivo auto-apt lo busque solo y lo instale mediante apt-get, para hacer esto ponemos en el directorio donde se encuentra el configure

[LEFT]```
sudo auto-apt run ./configure
```[/LEFT]
 Y listo!

Para que auto-apt sea efectivo debemos mantener sus bases actualizadas, esto lo hacemos mediante:

```
[LEFT]sudo auto-apt update 
sudo auto-apt updatedb
sudo auto-apt update-local[/LEFT]
 
```
 
Para mas información sobre auto-apt no te olvides de leer el [manpage]("http://www.debianadmin.com/manpages/autoaptmanpage.htm") del mismo.

---

### Post by Nemesis Teufel on 2006-11-26
gracias! =)

---

### Post by beuno on 2006-11-26
Muy bueno, no lo conocia.

---

### Post by jpmorelli on 2006-11-29
no lo probé, pero si hace lo que entendí es la solución a todos mis problemas !!! jamás logré compilar ni un Hello World !](*,)

---

