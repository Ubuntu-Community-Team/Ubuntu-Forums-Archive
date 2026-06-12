---
title: "El meu UBUNTU s'ha mort"
date: 2009-07-21
forum: Catalan Team
---

### Post by josepquegi on 2009-07-21
He instal·lat Ubuntu 9.04 Netbook Remix en un Toshiba NB100 (Netbook). A casa  meva tot va anar bé i no hi va haver cap problema en connectar a la meva wifi  (Router ADSL), però en marxar de casa, i anar a un lloc on no hi havia cap wifi  disponible, l'Ubuntu va quedar penjat i no es podia accedir a res. En tornar a  casa i detectar la meva wifi tot va tornar a anar bé, fins i tot desconnectant  el meu router (hi havien altres wifis disponibles).

Intentant provocar  l'error que es produïa fora de casa meva vaig deshabilitar la xarxa sense fils  (icono de barres dalt a la dreta). L'Ubuntu va quedar penjat, però ja per sempre  més!! Resulta que de les dues habilitacions de l'icono de barres (xarxa amb fils  i xarxa sense fils) la xarxa sense fils ha desaparegut i, per tant, ja no es pot  habilitar; tampoc es pot habilitar des d'enlloc més perquè no es pot accedir a  cap zona de l'escriptori.

Algú sap si es pot tornar a habilitar la xarxa  sense fils amb alguna seqüència de l'arrancada?
Es podria tornar a habilitar  aquesta xarxa editant (des d'un Ubuntu live) algun fitxer de  configuració?

Si algú em pot ajudar, ja li agraeixo per endavant.  Gràcies.

---

### Post by totalkiller on 2009-07-21
Es una cosa ben extranya, has provat de instal·lar el paquet linux-modules-backports-jaunty amb l'aptitude?
Jo tenia problemes amb la wifi fins que ho vaig instal·lar i desde llavors la wifi va prou be.
No he acabat d'entendre lo del escriptori amb tooot bloquejat, pero entra en mode terminal si no et va be el mode grafic.

---

### Post by Miquel Ubuntero on 2009-07-21
bones.
Alguns suggeriments:
Prova d'entrar amb un altre usuari o com a root. Ocasionalment pot passar que una conta de usuari no "rutlli" i amb un altre si puguis accedir. En aquest cas, des de l'altre usuari, si te privilegis d'administrador, podràs intentar reparar el problema.
Un problema d'escriptori que no funciona és pot reparar reinsta&#320;lant l'escriptori. Per exemple, amb Synaptic, reinsta&#320;lant el paquet gnome-desktop en el cas de tindre Ubuntu amb gnome.
Si no pots iniciar synaptic des de l'escriptori no funcional, pots provar de executar Alt-F2 i escriure sudo synaptic, per tal de intentar reinsta&#320;lar el que vulguis.
Si solventes el tema escriptori. Pel tema wifi, pots provar d'insta&#320;lar wifi-radar, disponible a synaptic i a afegeix/elimina. Es una alternativa per connectar-te a xarxes sense fil.
Un petit consell per properes insta&#320;lacions. Es una bona idea tindre més d'un usuari amb drets d'administrador i/o més d'un entorn d'escriptori per poder accedir al sistema en cas de fallada.
Salut i molta sort. ;)

---

### Post by indiosincracia on 2009-07-21
per anar eliminant;)
[http://www.softcatala.org/forum/viewtopic.php?f=3&t=2556](http://www.softcatala.org/forum/viewtopic.php?f=3&t=2556)

---

### Post by josepquegi on 2009-07-21
Ja he provat el que em dieu i el que m'han dit a Softcatalà, però segueix sense funcionar.
 
L'única manera d'accedir al sistema és a través del terminal (Ctrl+Alt+F1) just abans que surti l'escriptori ja que llavors es penja (Qui diu que l'Ubuntu no es penja?)

---

### Post by papapep on 2009-07-21
> (Qui diu que l'Ubuntu no es penja?) 

Tu.

Hauries de pujar [els fitxers que t'ha demanat en Cubells al fòrum de Softcatalà]("http://www.softcatala.org/forum/viewtopic.php?f=3&t=2556#p10442"), sinó no pot ajudar-te.

---

### Post by josepquegi on 2009-07-27
Gràcies als que heu intentat ajudar-me, però no hi ha hagut més manera de resoldre el problema que formatant la partició i tornant a instal·lar Ubuntu.

---

### Post by SiscoGarcia on 2009-07-27
> **josepquegi said:**
> ... no hi ha hagut més manera de resoldre el problema que formatant la partició i tornant a instal·lar Ubuntu.

Me n'alegro perquè tornes a tenir l'ubuntu funcional, però el que has fet no és resoldre el problema, ja que el que has fet és canviar de situació. Els xinesos diuen que si un problema no té solució no és un problema, i tu has fet una cosa semblant en reinstal·lar l'ubuntu (cosa que més d'un de nosaltres hem fet més d'un cop, però no és la manera més elegant de sortir-ne de la situació problemàtica).

---

### Post by MiquelBLL on 2009-07-28
Salutacions. Es fotut cuan hi ha coses que no marxen be i et trenques el cap i no hi ha manera. Sobre lo que et va desapareixer lo de la icona  de internet al quadre a mi tambe em va passar i no ho trobava la solucio la vaig trobar aqui al foro i era que tenies que afegir al quadre la icona ´Area de Notificació´.

---

