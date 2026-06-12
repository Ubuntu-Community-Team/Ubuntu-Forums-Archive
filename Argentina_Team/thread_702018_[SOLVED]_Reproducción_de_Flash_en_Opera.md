---
title: "[SOLVED] Reproducción de Flash en Opera"
date: 2008-02-19
forum: Argentina Team
---

### Post by aregnando on 2008-02-19
Hola, normalmente utilizo Firefox para navegar pero dado que experimento problemas en algunas paginas ej.: [www.clarin.com](www.clarin.com) la cual se me cuelga o se hace imposible de navegar por la lentitud con que se avanza en la misma es que decidí descargar Opera para probar este navegador.
Realmente me gustó bastante la velocidad con que carga pero me veo frente a problemas que ya había resuelto en Firefox tal como la reproducción de contenidos con flash, tengo instalado flashplugin-nonfree pero evidentemente esto no sirve, traté de solucionarlo tal como leí en algún foro copiando el archivo libflashplayer.so en la carpeta de plugins de opera pero no he podido ya que el sistema no me lo permite, realmente no se como acceder a esta carpeta como root y por tanto no tengo los permisos para poder pegar este archivo en opera.
Quisiera si alguien sabe de una solución para dejar a Opera funcionando correctamente se lo voy a agradecer.

---

### Post by faktorqm on 2008-02-19
user de opera reportandose: de memoria no me acuerdo, y encima no estoy en mi casa, pero cuando copias el archivo, si lo haces por terminal hacelo con "sudo" adelante, y mete tu contraseña. Si lo haces por interfaz grafica, hace ALT + F2, y ahi escribi "gksudo nautilus", mete tu contraseña y ahi te abre el nautilus en modo root. OJO, copia el archivo y cerralo, no t mandes ninguna macana.
Cuando lo copiaste, simplemente arranca el opera y sale andando. 
Salu2!!

---

### Post by aregnando on 2008-02-19
Hola faktorqm, creo que me mandé como bien dijiste una macana pero antes de hacer eso ya que por algo que hice perdí mi capacidad de administrar el sistema como root y me desaparecieron de sistema/administración/ todas las opciones administrativas como ser synaptic, administración de usuarios, etc. Lo peor es que no se que toqué para que suceda esto.
También en el listado de aplicaciones me desapareció agregar programas que figura siempre al final de la lista.
Esta vez la complique.

---

### Post by faktorqm on 2008-02-20
uhh estas complicadisimo. consejo, tomalo o dejalo, back-up al /home y reinstala. salu2!

---

### Post by aregnando on 2008-02-20
Gracias por el concejo, algo de eso me había temido ya que no puedo hacer nada y lo peor es que no se por que sucedió para poder evitarlo en el futuro.

---

### Post by faktorqm on 2008-02-20
si, o sea, lo que te dijo mauro22 no esta mal, de hecho es lo que yo hubiera hecho, el problema es que como no sabes que hiciste, no sabes volver atras. y despues de eso no sabes que secuelas te puede haber dejado en el sistema, capaz haces y no pasa nada, capaz haces y es todo un lio de permisos y no podes hacer nada. si queres probarlo para aprender antes de reinstalar, dale, total peor de lo que estas ahora no vas a estar.
Salu2!

---

### Post by aregnando on 2008-02-21
Bueno aquí estoy de nuevo con el sistema OK otra vez, Mauro22 y Faktorqm les hice caso y reinstalé, lamentablemente por más vueltas que le dí no encontré en ningún lado solución a lo que había hecho.
Volviendo al tema de Opera, ya copié el archivo libflashplayer.so a la carpeta de plugins de Opera y sigue igual que antes, no me carga flash, por ejemplo no puedo visualizar ningún video de Youtube
Acá copio lo que informa Opera sobre plugins:

[COLOR="Blue"][B]Plug-ins
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so

NS4PluginProxyapplication/x-opera-nsplugin	-
/usr/lib/opera/plugins/libnpp.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/flashplugin-nonfree/libflashplayer.so

Totem Web Browser Plugin 2.20.0audio/wav	wav
audio/x-wav	wav
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
audio/mpeg	mp3,mp2,mpga
application/ogg	ogg
audio/ogg	ogg
audio/x-ogg	ogg
video/ogg	ogg
video/x-ogg	ogg
application/x-nsv-vp3-mp3	nsv
video/flv	flv
/usr/lib/mozilla/plugins/libtotem-basic-plugin.so

RealPlayer 9application/smil	smi,smil
audio/x-pn-realaudio	ram,ra
video/vnd.rn-realvideo	rv
application/vnd.rn-realmedia	rm
application/vnd.rn-realaudio	ra,ram
audio/x-realaudio	ra
audio/x-pn-realaudio-plugin	rpm
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so

QuickTime Plug-in 7.2.0video/mp4	mp4
video/quicktime	qt,mov
image/x-macpaint	pntg
image/x-quicktime	pict, pict1, pict2
video/x-m4v	m4v
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so

Kaffeine Starter Pluginvideo/x-msvideo	avi
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
audio/mpeg	mp3,mp2,mpga
audio/x-mpegurl	m3u
video/quicktime	qt,mov
video/x-ms-asf-plugin	-
application/x-mplayer2	-
audio/x-ms-wma	wma
video/x-ms-wmv	wmv
audio/x-ogg	ogg
audio/x-pn-realaudio-plugin	rpm
video/x-mpeg	mpeg, mpg, mpe
audio/mpeg2	mp2
audio/x-mpeg2	mp2
audio/mpeg3	mp3
audio/x-mpeg3	mp3
audio/x-mpeg	mpa,abs,mpega
video/x-quicktime	mov,qt
video/msvideo	avi
audio/x-scpls	pls
/usr/lib/mozilla/plugins/kaffeineplugin.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/flashplugin-alternative.so

QuickTime Plug-in 6.0 / 7video/quicktime	qt,mov
video/quicktime	qt,mov
video/quicktime	qt,mov
application/smil	smi,smil
image/x-quicktime	pict, pict1, pict2
video/x-quicktime	mov,qt
application/x-quicktimeplayer	mov
/usr/lib/mozilla/plugins/mplayerplug-in-qt.so

mplayerplug-in 3.40video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4
audio/mpeg	mp3,mp2,mpga
audio/mpeg	mp3,mp2,mpga
audio/basic	au
application/ogg	ogg
audio/ogg	ogg
audio/x-ogg	ogg
application/x-nsv-vp3-mp3	nsv
video/x-mpeg	mpeg, mpg, mpe
audio/mpeg2	mp2
audio/x-mpeg2	mp2
audio/x-mpeg	mpa,abs,mpega
video/x-mpeg2	mpv2,mp2ve
video/3gpp	mp4,3gp
application/x-ogg	ogg
audio/flac	flac
audio/x-flac	flac
video/fli	fli,flc
video/x-fli	fli,flc
video/x-flv	flv
video/vnd.vivo	viv,vivo
audio/x-mod	mod
audio/x-basic	au,snd
/usr/lib/mozilla/plugins/mplayerplug-in.so

DivXÂ® Web Playervideo/divx	divx
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so

DivX Browser Plug-Invideo/divx	divx
video/vnd.divx	divx
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

Windows Media Player Pluginaudio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi
video/x-ms-asf	asf,asx
application/asx	-
video/x-ms-asf-plugin	-
application/x-mplayer2	-
video/x-ms-wm	wm
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv
video/msvideo	avi
application/x-ms-wmv	wmv,*
audio/x-ms-wmv	wmv,*
video/x-ms-wmp	wmp,*
application/x-drm-v2	asx,*
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so

Windows Media Player Plug-in 10 (compatible; Totem)video/x-msvideo	avi
video/x-ms-asf	asf,asx
application/asx	-
video/x-ms-asf-plugin	-
application/x-mplayer2	-
video/x-ms-wm	wm
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv
video/x-wmv	wmv
application/x-ms-wms	wms
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so[/B]
[/COLOR]

Espero sea de utilidad para que a alguien se le ocurra que puede estar faltando.
Gracias.

---

### Post by leo_rockway on 2008-02-21
Yo era fana de Opera y dejé de usarlo por no ser libre. Flash siempre me funcionó perfecto. Ahora uso Konqueror y noté algo que quizás pueda ayudar: la última versión de Flash NO me funciona con Konqueror, así que lo que hice fue rescatar el libflashplayer.so de una versión anterior. A lo mejor Opera tiene el mismo problema.

No puedo dejar este post sin maldecir a Flash... ¡MALDITO FLASH!

---

### Post by faktorqm on 2008-02-22
Hola, yo en casa veo todo, ahora toy en el job, llego a casa y te digo. Salu2!!

---

### Post by Thalskarth on 2008-02-22
Hola...

Mirá, la solucion más sencilla.. es que instales el flash player (paquete llamado flashplugin-nonfree) y fijate que funcione en firefox. Si ahi anda, entoces con bajarte el Opera 9.5b (que a mi me funciona perfectamente) ya lo toma sin dramas a todo lo que sea flash.


Sino, fijate de copiar el archivo "libflashplayer.so" (suele estar en /usr/lib/firefox/plugins o en /usr/lib/flashplugin-nonfree) a la carpeta de plugins del firefox(/usr/lib/firefox/plugins) o incluso a la del mismo opera (/usr/lib/opera/plugins) o incluso a cualquiera de las carpetas de plugins que tiene el opera.

Por defecto, el opera los busca en:

[LIST]
[*]/usr/lib/opera/plugins
[*]/usr/lib/flashplugin-nonfree
[*]/usr/lib/mozilla/plugins
[*]/usr/lib/netscape/plugins-libc6
[/LIST]

Asi que conque este en alguna de esas carpetas deberia de funcionar* ;D

Aunque como dije, con el 9.5b ya lo toma desde el firefox y listo

---

### Post by aregnando on 2008-02-22
Ok, gracias Thalskarth, voy a tratar bajando esa versión de Opera ya que todas las otras soluciones ya las hice y ninguna me dió resultado, luego te cuento como me va con esta nueva versión.

---

### Post by aregnando on 2008-02-22
Hola, finalmente tal como me sugirió Thalskarth, bajé Opera 9.5b y una vez instalado reconoce los plugins sin ningún problema, ya reproduce flash de lo mejor.
Muchas gracias ya que este navegador es excelente sin desmerecer a Firefox pero me carga las páginas más rápido y en algunas en las cuales Firefox se cuelga, Opera sale andando perfecto.
Saludos a todos.

---

### Post by Thalskarth on 2008-02-23
Me alegra se te halla solucionado el problema.

De paso, si queres fijate e[sta pagina]("http://es.ghacks.net/2007/04/06/10-consejos-para-acelerar-opera/") donde hay un tuto para configurar el opera de forma que sea aun más rapido...

personalmente, basado en ese tuto yo he modificado algunas cosas y otras las he adaptado segun mi gusto... por ejemplo uso un cache de 500megas..., y actualizo imagenes cada semana y paginas cada hora... con esto, mi opera realmente vuela

---

### Post by aregnando on 2008-02-25
Gracias Thalskarth, ya puse en práctica varios ellos.
Saludos.

---

