---
title: "Ubuntu no abre documentos"
date: 2008-05-02
forum: Argentina Team
---

### Post by _kAz_ on 2008-05-02
Gran inconveniente gran!!!

No puedo abrir ciertos documentos en Ubuntu, por ejemplo los archivos .doc, .odt de openoffice,  o los .svg de Inkscape. Hago doble click pero no sucede nada así que no me queda otra que ir al programa respectivo y abrirlo desde ahí.

Las imágenes si pueden abrirse -creo que usa F-Spot-, sin embargo cuando hago click derecho y las quiero "abrir con GIMP" tampoco hace nada.

Help!

---

### Post by faktorqm on 2008-05-02
guau! a mi me paso eso una vez tambien, y no lo pude arreglar :(

hace una cosa para intentar ver cual es el error, abri una consola y tipea por ejemplo:

```
inkscape blabla.svg
```
```
gimp blabla.jpg
```

a ver que mensaje te tira en la consola. Salu2!!

---

### Post by _kAz_ on 2008-05-03
> **faktorqm said:**
> guau! a mi me paso eso una vez tambien, y no lo pude arreglar :(

hace una cosa para intentar ver cual es el error, abri una consola y tipea por ejemplo:

```
inkscape blabla.svg
```
```
gimp blabla.jpg
```

a ver que mensaje te tira en la consola. Salu2!!

Hice lo que me dijiste desde consola Y LO ABRE!!!

Pero cuando le hago doble click en el icono no pasa nada!!! :-k

---

### Post by faktorqm on 2008-05-04
uhh y entonces proba click derecho sobre el archivo -> "abrir con otra aplicacion" y elegi el gimp digamos y ponele que sea la predeterminada. A ver que pasa. Salu2!

---

### Post by _kAz_ on 2008-05-04
Probe y es muy raro lo que pasó.

Intente acceder a un archivo de texto .odt con "Abrir con otra aplicación > OpenOffice Writer" y no sucedió nada. Lo raro es que cuando hice lo mismo pero con el Gedit sí abrio el programa -de todas formas no lo leyo porque es otro formato-.

No se me ocurre qué puede ser :S

---

### Post by _kAz_ on 2008-05-05
I made it!!!! :D

Me fije bien y habia algo particular, los archivos no se abrían con programas "grandes" pero sí con otros más simples. Por ejemplo un .png no lo podía hacer andar con el GIMP pero sí con el Visor de Imágenes o el F-Spot; lo mismo ocurría con un archivo de texto, sí se podía con el GEdit pero no con OpenOffice.

Incluso me iba a las propiedades y de ahí elegía el programa en "abrir con", pero seguía todo igual...

Solución: me fui al editor de menú, copie el comando que aparece tanto para OpenOffice Writer como para Inkscape (los 2 que necesitaba), me fui a los archivos, y ahí: propiedades > abrir con > utilizar otro comando > pegué el comando y leeestooooo!!!

Ya le pueden poner el [SOLVED] si quieren ;)

---

