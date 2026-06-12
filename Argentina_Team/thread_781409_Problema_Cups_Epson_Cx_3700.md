---
title: "Problema Cups Epson Cx 3700"
date: 2008-05-04
forum: Argentina Team
---

### Post by totoloco on 2008-05-04
Gente, tengo un problema con la impresora.
Estoy con Cups, la impresora es una Epson Cx 3700.

Intento imprimir y no sale nada, en el webserver de cups el trabajo está parado, y la impresora tiene el siguiente mensaje:

EPSON_Stylus_CX3700_USB_1 "ijsgutenprint: the version of Gutenprint software installed (5.0.2) does not match the PPD file (5.0.1)."

el /var/log/cups/error_log tiene lineas tales como:

E [04/May/2008:09:13:32 -0300] [Job 64] ijsgutenprint: bad key code -4
E [04/May/2008:09:13:32 -0300] [Job 64] ijsgutenprint: the version of Gutenprint software installed (5.0.2) does not match the PPD file (5.0.1).

Parece q hay un desfasaje entre el Gutenprint y la versión de los PPD (???)

Intenté actualizar los PPD con cups-genppdupdate.5.0
"No Gutenprint PPD files to update."

Regenerarlos con cups-genppd.5.0 y vuelvo a lo mismo, como q no genera nada nuevo.

Yo no se si fué con el upgrade a HH, no estoy seguro, xq no imprimo hace bastante.
A alguien ya le ocurrió?
Algun hueso para tirarme.

salU

---

### Post by totoloco on 2008-05-04
SOLVED
Solucionado gracias al [SIZE="3"]juan-arg[/SIZE] del irc ubuntu-es y el irc ubuntu-ar.

sudo apt-get purge cupsys cupsys-driver-gutenprint
sudo apt-get install cupsys cupsys-driver-gutenprint

salU

---

