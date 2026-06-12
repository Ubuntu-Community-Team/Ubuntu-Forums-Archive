---
title: "Ver el nivel de tinta en mi impresora HP F380"
date: 2008-01-05
forum: Argentina Team
---

### Post by jclevien on 2008-01-05
Hola que tal,

Estuve intentando conectarme a la impresora con un programa que se llama ink. Para que funcione, al mismo hay que especificarle el device correspondiente al ink. El problema es que no se cual es el device.

En la configuración "Imprimiendo" del menú de Xubuntu, aparece el siguiente string:

hp:/usb/Deskjet_F300_series?serial=BR77SGN0GV04KH

que obviamente, no marca un device.
El campo Ubicación está vacío.

¿Podrían darme una pista para poder usar el programa ink?

Muchas gracias.


Juan

---

### Post by rojojuan on 2008-01-05
Cómo está conectada, al puerto paralelo o usb?

---

### Post by jclevien on 2008-01-05
Hola rojojuan,

Está conectada al puerto USB.
Gracias.


Juan

---

### Post by rojojuan on 2008-01-05
> **jclevien said:**
> Hola rojojuan,

Está conectada al puerto USB.
Gracias.


Juan

Para ver la ubicación:
Sistema
Administración
Seleccioná tu impresora
En la casilla URI del dispostivo te lo indica.

---

### Post by jclevien on 2008-01-05
Que tal rojojuan,

No tengo los accesos que mencionás en el Xubuntu.
Solo tengo lo que dije, "Imprimiendo", y el URI es el publicado: hp:/usb/Deskjet_F300_series?serial=BR77SGN0GV04KH.

Con lo cual no ayuda mucho, como verás.

Ahora me estoy acordando del comando dmesg, investigaré por allí.

Saludos.


Juan

---

### Post by rojojuan on 2008-01-06
No conozco Xubuntu, pero probá en consola usb_printerid. En Ubuntu funciona.
Espero te sirva.

---

