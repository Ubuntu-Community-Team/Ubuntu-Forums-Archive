---
title: "[SOLVED] Como actualizar sin internet"
date: 2008-03-23
forum: Argentina Team
---

### Post by Mauro22 on 2008-03-23
Buenas!!


Tengo un problemon.
Ayer se actualizo hardy... todo bien hasta que reincie.


No se conecta mas... se queda en "conectando a red inalambrica......" 30, 60, 100 minutos. Supongo que habra sido alguna actualizacion.


Probe con varios kernel, nada.


Como puedo hacer ???


:lolflag:
Gracias!!

Felices Pascuas :KS

---

### Post by Sam Lars on 2008-03-23
Que dice
```
lspci
```

---

### Post by Mauro22 on 2008-03-23
La placa es USB (Wireless G USB Adapter), la reconoce y todo (lsusb) pero el problema es que se traba al intentar conectarse.


Ahora estoy usando Fedora 8 y anda muy bien.

---

### Post by Sam Lars on 2008-03-23
Parece que Fedora funciona bien con cosas como esto.
No haces nada por la placa en 7.10?  Has probado ndiswrapper (ndisgtk)?

---

### Post by Mauro22 on 2008-03-24
Todavia no probe el ndiswrapper porque parece que me voy a quedar con fedora.

Hardy Heron anda muy bien, pero fedora lo supera un poco.

Gracias, Sam Lars!


Editado:
Lo solucioné yendo a Sistema -> Admiistracion -> Red, Desactivar modo itinerante y configurar manualmente.
Actualizar el sistema


Saludos!

---

