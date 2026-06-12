---
title: "modem detection"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by futaxi on 2007-01-09
Hola, ubunteros. Instale la version 6.06 lts, y me detectaba y trabajaba perfectamente con el modem bona linden ef56rii, pero me decidí a instalar la ver. 6.10, y ya no hay detección. Conseguí instalar manualmente el modem, pero sólo me trabaja a 9800 ?? kbtis, cuando en LTS iba a 52000.  Tiene alguien la solución?? Muchas gracias.

---

### Post by luvinit on 2007-01-09
Lo siento, no hablo Espanol, amigo.

---

### Post by ieee488 on 2007-01-09
I believe his modem was detected and working in Ubuntu 6.06 but not in Ubuntu 6.10.
Then he manually installed the modem. Not sure what that means. But apparently he can connect only at 9800 but not at 52000.

---

### Post by Mark_in_Hollywood on 2007-01-09
In a terminal (or console)

sudo wvdialconfig /etc/wvdial.conf

entonces:

sudo gedit /etc/wvdial.conf


entonces

addamas

su: nombre en isp, el numero de telefono a isp, y su password

lo siento! me espanos nooo es bueno!

---

