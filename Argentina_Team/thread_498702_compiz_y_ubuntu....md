---
title: "compiz y ubuntu..."
date: 2007-07-11
forum: Argentina Team
---

### Post by Miriknell on 2007-07-11
Buenas, quise instalar compiz como dice en esta url: 
[http://blog.unlugarenelmundo.es/2007/06/26/509/](http://blog.unlugarenelmundo.es/2007/06/26/509/)

sigo todos los pasos, y en el ultimo me dice lo siguiente......
que puede ser??????

marcos@marcos:~$ sudo compiz --replace -c emerald &
[4] 8046
marcos@marcos:~$ Backend     : ini
Integration : true
Profile     : default
Adding plugin opacify (opacify)
Adding plugin atlantis (atlantis)
Adding plugin trailfocus (trailfocus)
Adding plugin scalefilter (scalefilter)
Adding plugin vpswitch (vpswitch)
Adding plugin firepaint (firepaint)
Adding plugin fadedesktop (fadedesktop)
Adding plugin cheatsheet (cheatsheet)
Adding plugin wall (wall)
Adding plugin snap (snap)
Adding plugin splash (splash)
Adding plugin crashhandler (crashhandler)
Adding plugin annotate (annotate)
Adding plugin regex (regex)
Adding plugin inotify (inotify)
Adding plugin keybinding (keybinding)
Adding plugin addhelper (addhelper)
Adding plugin ring (ring)
Adding plugin wobbly (wobbly)
Adding plugin 3d (3d)
Adding plugin glib (glib)
Adding plugin imgjpeg (imgjpeg)
Adding plugin thumbnail (thumbnail)
Adding plugin cubereflex (cubereflex)
Adding plugin clone (clone)
Adding plugin winrules (winrules)
Adding plugin gotovp (gotovp)
Adding plugin resizeinfo (resizeinfo)
Adding plugin extrawm (extrawm)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin dbus (dbus)
Adding plugin notification (notification)
Adding plugin fakeargb (fakeargb)
Adding plugin workarounds (workarounds)
Adding plugin fade (fade)
Adding plugin switcher (switcher)
Adding plugin cube (cube)
Adding plugin snow (snow)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin neg (neg)
Adding plugin plane (plane)
Adding plugin colorfilter (colorfilter)
Adding plugin zoom (zoom)
Adding plugin place (place)
Adding plugin quickchange (quickchange)
Adding plugin video (video)
Adding plugin reflex (reflex)
Adding plugin expo (expo)
Adding plugin svg (svg)
Adding plugin showdesktop (showdesktop)
Adding plugin tile (tile)
Adding plugin mousegestures (mousegestures)
Adding plugin fs (fs)
Adding plugin decoration (decoration)
Adding plugin wallpaper (wallpaper)
Adding plugin screensaver (screensaver)
Adding plugin bench (bench)
Adding plugin resize (resize)
Adding plugin water (water)
Adding plugin rotate (rotate)
Adding plugin group (group)
Adding plugin put (put)
Adding plugin kiosk (kiosk)
Adding plugin widget (widget)
Adding plugin animation (animation)
Adding plugin flash (flash)
Adding plugin text (text)
Adding plugin png (png)
Adding plugin scaleaddon (scaleaddon)
Adding core settings (General Options)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Initializing core options...done
Initializing minimize options...done
Initializing move options...done
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
Initializing zoom options...done
Initializing place options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Advertencia del gestor de ventanas: La ventana 0x3002016 () ha establecido la propiedad MWM indicando que no es redimensionable, pero configuró el tamaño mínimo a 488 x 278 y el tamaño máximo a 2147483647 x 2147483647 ; esto no tiene mucho sentido.
Advertencia del gestor de ventanas: La ventana 0x3002016 () ha establecido la propiedad MWM indicando que no es redimensionable, pero configuró el tamaño mínimo a 488 x 278 y el tamaño máximo a 2147483647 x 2147483647 ; esto no tiene mucho sentido.

---

### Post by gepatino on 2007-07-12
> **Miriknell said:**
> Buenas, quise instalar compiz como dice en esta url: 
[http://blog.unlugarenelmundo.es/2007/06/26/509/](http://blog.unlugarenelmundo.es/2007/06/26/509/)

sigo todos los pasos, y en el ultimo me dice lo siguiente......
que puede ser??????

marcos@marcos:~$ sudo compiz --replace -c emerald &


Fijate que en el último paso de las instrucciones no usa sudo para iniciar el cmompiz. El compiz pasa a remplazar al gestor de ventanas, asi que si lo ejecutás como root no va a poder tomar control de tu sesión porque seguro le faltan varibles de entorno, etc.

Ejecuta simplemente:

compiz --replace -c emerald &

---

### Post by Miriknell on 2007-07-12
> **gepatino said:**
> Fijate que en el último paso de las instrucciones no usa sudo para iniciar el cmompiz. El compiz pasa a remplazar al gestor de ventanas, asi que si lo ejecutás como root no va a poder tomar control de tu sesión porque seguro le faltan varibles de entorno, etc.

Ejecuta simplemente:

compiz --replace -c emerald &


Es verdad... igualmente, un compañero del laburo q lo pudo instalar me dice que cambie

KEY=81836EBF; gpg –keyserver subkeys.pgp.net –recv [COLOR="Red"]$KEY[/COLOR] && gpg –export –armor [COLOR="Red"]$KEY [/COLOR]| sudo apt-key add -

por 

KEY=81836EBF; gpg –keyserver subkeys.pgp.net –recv [COLOR="Red"]81836EBF [/COLOR]&& gpg –export –armor [COLOR="Red"]81836EBF [/COLOR]| sudo apt-key add -

Hoy pruebo.... 

Gracias!

---

