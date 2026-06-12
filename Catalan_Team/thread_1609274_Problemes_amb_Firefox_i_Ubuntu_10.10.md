---
title: "Problemes amb Firefox i Ubuntu 10.10"
date: 2010-10-30
forum: Catalan Team
---

### Post by Contaboy on 2010-10-30
Bon dia,

Estic provant el nou Ubuntu 10.10 i tinc problemes en la visualització de videos

Vaig actualitzar el Adobe Flash i ho he sol·lucionat però ara no puc veure certes web com [www.illimitux.net](www.illimitux.net), [www.sport.es](www.sport.es)

En totes em diu que no troba el servidor, bé en la del diari sport em redirigeix a un altra pàgina.

Per instal·lar el Adobe Flash primer el vaig baixar i el vaig substituir a usr/lib/flashplugin-installer

Aquí van començar els meus problemes

Al tenir problemes primer vaig desinstalar amb els respositoris el flashplugin-installer i el vaig reinstalar juntament amb flahplugin-nonfree (com es recomana als foros de ubuntu)

Veient que no es solucionava vaig optar per la solució de [http://www.laconsolablog.com/2009/02/06/instalar-flash-player-10-en-ubuntu-64-y-32-bits/](http://www.laconsolablog.com/2009/02/06/instalar-flash-player-10-en-ubuntu-64-y-32-bits/) i ara veig videos en youtube però en megavideo em salten en mode finestra i no es veuen a pantalla complerta.

Agrairia una ajudeta

---

### Post by wgarcia on 2010-10-30
Aquí hi ha una solució que alguns diuen que arregla el teu problema:

1. Obre una terminal (o ALT+F2) i entra:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

2. Afegeix la línia següent abans de l'última línia:
export GDK_NATIVE_WINDOWS=1

3. Desa i reinicia Firefox, o millor reinicia l'ordinador.

A veure si t'ho arregla a tu també.

---

### Post by Contaboy on 2010-11-16
Gràcies.

No se com s'ha solucionat sol al reiniciar la màquina per enesima vegada. 

De totes maneres he trobat els plugins d'ambdós per firefox amb el que m'estalvio llençar el cacaoweb cada vegada que inicio.

---

