---
title: "Vinagre"
date: 2009-04-19
forum: Catalan Team
---

### Post by venusfenix on 2009-04-19
buenas,

tinc un laptop ACER AMD 64bitx2 amb ubuntu intrepid ibex, i vull aprende a utulitzar el VINAGRE, pero trobo, o no soc capaç de fer-lo servir.

la meva intencio que conectar-me remotament pero de manera local als altres 2 ordinadors que tinc amb W XP i vista.

algu coneix alguna pagina que sigui util?

moltes gracies,

---

### Post by Miquel Ubuntero on 2009-04-19
Bones.
No conec aquest Vinagre, però si vols connexió remota també pots provar el vnc que be integrat a Ubuntu. A mi m'ha anat molt be.
Aquí en parlen: [http://www.guia-ubuntu.org/index.php?title=VNC](http://www.guia-ubuntu.org/index.php?title=VNC)
Salut!

---

### Post by Xispa on 2009-04-19
Jo, per connectar-me a màquines Windows remotament utilitzo el Client de terminal server, que el pots trobar a *Aplicacions > Internet > Client de Terminal Server*. Si no el tens instal·lat, doncs *Afegeix/Elimina aplicacions...* i busca per 'Terminal Server'

Només has de tenir en compte que a Windows, has d'habilitar l'accés remot (*Inicio > Panel de control > Sistema* i pestanya *Remoto*), l'usuari de windows ha de tenir paraula de pas i el protocol que has d'utilitzar al Client de Terminal Server és el RDPv5.

Salut,
Jordi

---

### Post by SiscoGarcia on 2009-04-19
Em sembla molt que tots tres esteu parlant de la [mateixa cosa]("http://ubuntuforums.org/showthread.php?t=1045456"); el client de terminal server que apareix a la pestanya d'internet a l'apartat d'aplicacions és el que s'anomenava [Vino]("http://miguiaubuntu.wordpress.com/2007/09/14/administracion-remota-grafica-en-ubuntu-vino/") i en l'actualitat ha passat a anomenar-se [Vinagre]("http://projects.gnome.org/vinagre/").

Pel que fa a algun tutorial, a més de l'opció de fer "vinagre man" a consola, pots provar què diu [aquí]("http://linux.die.net/man/1/vinagre"), o googlejant una mica.

---

### Post by papapep on 2009-04-20
No ben bé, Sisco.

[Vino]("http://packages.ubuntu.com/search?keywords=vino&searchon=names&suite=intrepid&section=all") és el servidor de VNC per a Gnome.

[Vinagre]("http://packages.ubuntu.com/search?keywords=vinagre&searchon=names&suite=intrepid&section=all"), n'és el client per a Gnome.

I [tsclient]("http://packages.ubuntu.com/search?keywords=tsclient&searchon=names&suite=intrepid&section=all") (el que hi ha sota "Client de terminal Server", és un client multiprotocol que permet connectar-se a escriptoris remots per VNC, RDP, ICA i XDMCP (per a més informació, la wikipedia és la vostra amiga...).

:)

---

### Post by SiscoGarcia on 2009-04-20
> **papapep said:**
> No ben bé, Sisco.

:oops: Perdó per la confusió que puc haver creat. Se m'escapaven aquests detalls. Gràcies per l'aclariment ;)

---

### Post by akyra on 2009-04-22
Hola a tothom.

Jo em connecto des de casa a la feina, a XP, W2003 Server, amb el Client de terminal server i em funciona molt bé. Abans faig una conexió VPN
El protocol que el·legeixo és o VNC o RDP depenent de la configuració que tinc a la feina.

Salutacions

---

