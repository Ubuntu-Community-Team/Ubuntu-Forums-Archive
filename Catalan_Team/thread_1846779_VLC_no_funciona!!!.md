---
title: "VLC no funciona!!!"
date: 2011-09-19
forum: Catalan Team
---

### Post by montonec on 2011-09-19
A veure si em podeu ajudar... Vaig estar editant els fitxers de configuració del VLC per tal de poder usar una aplicació d'Android com a control remot. AA part que no vaig sortir-me'n de configurar l'aplicació des de llavors el VLC no arrenca. Si el vull cridar des del terminal, em surt el següent misssatge d'error:

tonicantos@tonicantos-laptop:~$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
[0x93e39ec] main interface: creating httpd
[0x93e39ec] main interface error: socket bind error (Permission denied)
[0x93e39ec] main interface error: socket bind error (Permission denied)
[0x93e39ec] main interface error: cannot create socket(s) for HTTP host
[0x93e39ec] oldhttp interface error: cannot listen on :8080
[0x93e39ec] main interface error: no suitable interface module
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x93c4904] main interface: creating httpd
[0x93c4904] main interface error: socket bind error (Permission denied)
[0x93c4904] main interface error: socket bind error (Permission denied)
[0x93c4904] main interface error: cannot create socket(s) for HTTP host
[0x93c4904] oldhttp interface error: cannot listen on :8080
[0x93c4904] main interface error: no suitable interface module
[0x9313164] main libvlc error: interface "default" initialization failed

He provat de desintal·larlo i tornar-lo a instalar, esborrent tots els paquets des del Synaptic però no hi ha manera....

Gràcies!

---

### Post by CarlesOriol on 2011-09-19
Elimina o modifica els arxius de configuració a:

/home/elteuusuari/.config/vlc

---

### Post by montonec on 2011-09-24
Gracies Carles!

Al final me'n vaig atipar i he reinstal·lat Ubuntu ... Ara funciona el VLC però no puc reproduir dvds...

---

### Post by wgarcia on 2011-09-25
Has instal·lat el paquet "ubuntu-restricted-extras"? Aquest és el que porta els codecs de DVD, que estan protegits per patents i són propietaris i per aquesta raó no venen per defecte.

---

### Post by montonec on 2011-10-06
L'he instal·lat i ara sí!

Gràcies!

---

