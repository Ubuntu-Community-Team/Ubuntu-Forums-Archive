---
title: "Problemas en Incio de Sesion"
date: 2008-05-01
forum: Argentina Team
---

### Post by PatoDB on 2008-05-01
Hola Gente!!!

Como les va??

La verdad, no me gusta molestarlos, pero ya no se que hacer. :P

El problema es el seguiente:

Cuando inicio la sesion, Nombre usuario, contraseña, enter.... Entra, me aparece el Wallpaper y no carga mas nada. Ni iconos, ni barra, ni nada.
Solo puedo entrar (como ahora) en "Gnome a Prueba de Fallos"

Funciono bien un dia (lo tengo instalado hace dos.. :P), no tenia problemas ni nada.

Cuando comenzo el problema, en un principio, solo me cargaba los Desklets y el Cairo-Clock, por lo que la primera cosa que pense, es que habia un problema ahi. Asi que fui a las aplicaciones que se inician al principio y desactive todo, saque los Desklets y el Cairo-Clock. (todo esto en A prueba de fallos) Vuelvo a reiniciar en sesion comun y corriente, y me abria el Cairo-Clock 0.0, y lo habia desactivado!

Asi que pense que era algo del Cairo que me trababa, asi que fui a Agregar o Quitar Aplicaciones y lo desinstale. Reinicie, entre en sesion comun y corriente, y por suerte no me abrio mas el Cairo :P, pero ahora directamente solo aparece el Wallpaper y nada mas.


Lo unico que hice antes que me dejara de funcionar, fue instalar el mesa-utils, porque queria hacer una comparacion con la PC de un amigo y necesitaba usar el glxgears.




Si alguien pudiera ayudarme, bienvenidas sean todas las sugerencias...


Desde ya, gracias!!!!


^^

--------------------------------------

Sincronice mi reloj con el de la PC, loguie a las 18.18 hasta las 18.20.

No paso nada, cargo el Wallpaper y nada mas..

A las 18.20 volvi a loguear como A Prueba de Fallos, fui a Procesos del Sistema, y esto es lo que dice a esa hora...


**user.log**

> May  1 18:18:04 patodb-desktop pulseaudio[5479]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May  1 18:20:01 patodb-desktop pulseaudio[5479]: module-x11-xsmp.c: Failed to open connection to session manager: IO error occured opening connection
May  1 18:20:01 patodb-desktop pulseaudio[5479]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
May  1 18:20:16 patodb-desktop pulseaudio[5637]: pid.c: Stale PID file, overwriting.
May  1 18:20:16 patodb-desktop pulseaudio[5637]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.




**auth.log**

> May  1 18:18:00 patodb-desktop gdm[5175]: pam_unix(gdm:session): session opened for user patodb by (uid=0)
May  1 18:20:01 patodb-desktop gdm[5175]: pam_unix(gdm:session): session closed for user patodb
May  1 18:20:05 patodb-desktop gdm[5580]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  1 18:20:05 patodb-desktop gdm[5580]: PAM [error: /lib/security/pam_smbpass.so: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio]
May  1 18:20:05 patodb-desktop gdm[5580]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  1 18:20:15 patodb-desktop gdm[5580]: pam_unix(gdm:session): session opened for user patodb by (uid=0)




**daemon.log**

> May  1 18:18:09 patodb-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
May  1 18:18:09 patodb-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May  1 18:20:01 patodb-desktop gdm[5175]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
May  1 18:20:15 patodb-desktop gdm[5580]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May  1 18:20:15 patodb-desktop gdm[5580]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
May  1 18:20:15 patodb-desktop gdm[5626]: Gtk-WARNING: Ignoring the separator setting 
May  1 18:20:21 patodb-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
May  1 18:20:21 patodb-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 




**messages**

> May  1 18:18:04 patodb-desktop pulseaudio[5479]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May  1 18:20:16 patodb-desktop pulseaudio[5637]: pid.c: Stale PID file, overwriting.
May  1 18:20:16 patodb-desktop pulseaudio[5637]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.




**syslog**

> May  1 18:18:04 patodb-desktop pulseaudio[5479]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May  1 18:18:09 patodb-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
May  1 18:18:09 patodb-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May  1 18:20:01 patodb-desktop pulseaudio[5479]: module-x11-xsmp.c: Failed to open connection to session manager: IO error occured opening connection
May  1 18:20:01 patodb-desktop pulseaudio[5479]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
May  1 18:20:01 patodb-desktop gdm[5175]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
May  1 18:20:15 patodb-desktop gdm[5580]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May  1 18:20:15 patodb-desktop gdm[5580]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
May  1 18:20:15 patodb-desktop gdm[5626]: Gtk-WARNING: Ignoring the separator setting 
May  1 18:20:16 patodb-desktop pulseaudio[5637]: pid.c: Stale PID file, overwriting.
May  1 18:20:16 patodb-desktop pulseaudio[5637]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May  1 18:20:21 patodb-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
May  1 18:20:21 patodb-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

---

### Post by atatiducken on 2008-05-02
mmm, si habias hecho un backup de tu xorg.conf proba con eso, restituilo como "original"; y saca del inicio todo lo q pienses q puede ser problematico y ahi vas viendo
saludos

---

