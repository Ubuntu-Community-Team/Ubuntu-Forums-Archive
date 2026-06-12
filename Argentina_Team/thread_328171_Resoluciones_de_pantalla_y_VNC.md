---
title: "Resoluciones de pantalla y VNC"
date: 2006-12-30
forum: Argentina Team
---

### Post by Teno on 2006-12-30
Bueno, les cuento la situacion:

Tengo una PC un poco viejita que es la que tiene el Ubuntu cargado y me conecto a esa maquina por VNC (simplemente por un tema de compatibilidad, insluso puedo entrar desde una Palm TX)

Me di cuenta que cuando la PC arranca sin un monitor conectado, no puedo pasar la resolucion mas alla de los 640 x 480, cosa que es muy molesto, me encantaria poder utiliarla en la resolucion que se me cante el Ubuntu.

El tema es, COMO????

Alguna idea?

---

### Post by beuno on 2006-12-30
Edita /etc/X11/xorg.conf

Y sacale las opciones de resolucion que no quieras usar, y deja la(s) que si.
Reinicias.
Listo.

---

### Post by Teno on 2006-12-30
Si!!!

Buenisimo!!!

Ya habia encontrado y las borre, pero siempre me aparecia todo el tema en 640 x 480 y sin opcion a cambiarlo... es como que cuando no detecta el monitor, se pone en modo "super recontra compatibilidad por las dudas que ejecutes ubuntu en una 286"

Lo que hice fue ver una xorg.conf de otra maquina y en la parte "Monitor" le agregue:

            HorizSync          30-96
            VertRefresh        50-160

Lo que supongo que son las lineas de resolucion del monitor, forzadas.

Paso siguiente, reinicie en mi caso el equipo, ya que no me sale reiniciar la X solamente.

Una vez hecho esto, me meti en resolucion de pantalla, esta vez me aparecieron todas, seleccione 800 x 600, por decir una y marque la opcion "utilizar como predeterminado" y santo remedio, cada vez que me meto en la X por VNC me arranca en 800 x 600...

Hermoso, que quiere que le diga...](*,)

---

### Post by jpmorelli on 2006-12-31
Teno , para reiniciar la X solamente nada mas facil que CTRL+ALT+Backspace ;)

---

### Post by Teno on 2006-12-31
Si, pero el tema es que a travez del cliente PalmOS de VNC se complica para mandar esa combinacion de teclas...

---

