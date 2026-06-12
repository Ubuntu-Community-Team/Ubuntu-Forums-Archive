---
title: "[SOLVED] No em detecta la acceleració gràfica"
date: 2007-10-23
forum: Catalan Team
---

### Post by montagú on 2007-10-23
Bona tarda.

Primer presentarme ja que soc nou per aquí. El meu problema es que s'em va desconfigurar la tarjeta gràfica al conectar un monitor extern al portàtl i al final vaig poder recuperar-la reconfigurant xorg.conf, el problema es que no em detecta la acceleració gràfica i no se com fer-ho.

```
montagu@montagu-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting  IBGL_DEBUG=verbose)
```


La tarjeta es una Intel 950GM (em detecta la 945GM) i al intentat configurar-la gràficament em dona un missatge [(foto)]("http://picasaweb.google.com/albert.campo/Popurri/photo#5123810250452499474") i no es queda memoritzada la configuració.

Tb he detectat que a /etc/X11 tinc molts arxius xorg.conf:

xorg.conf
xorg.conf.1
xorg.conf.2
xorg.conf.3
xorg.conf.4
xorg.conf.5

xorg.conf.20071020181623 (hi han uns quants i el número es 2007/10/20 a l'hora 18:16:23)

xorg.conf.failsafe
xorg.conf.1.failsafe
xorg.conf.2.failsafe
xorg.conf.3.failsafe
xorg.conf.4.failsafe
xorg.conf.5.failsafe

Els puc eliminar? amb quins m'he de quedar?

Moltes gracies per anticipat!!!

---

### Post by papapep on 2007-10-23
Abans que res benvingut.

Jo el que faria és mirar la data dels antics xorg.conf, buscar el que tingui la data més propera (però d'abans) a la data de la hecatombe i fer-lo servir per a veure si funciona (recorda fer abans una còpia de seguretat de l'actual, que com a mínim et deixa entrar a l'entorn gràfic).

---

### Post by montagú on 2007-10-23
Ja els he elimintat i res, el problema es que no he trobat cap codi per activar la acceleració gràfica per a Intel.

Si veig que no ho soluciono em tocarà formatejar aviat pq m'avia acostumbrat al Compiz i al AWN :P

Gracies!

---

### Post by nickpage on 2007-10-23
Segons he llegit a la guia ubuntu, el XGL que segurament tens instal·lat no te Direct Rendering, ara be, aquest si es necessari per a funcionar.

El que has de fer es executar l'aplicació que vulguis amb una llançadora o un terminal amb el paràmetre DISPLAY=:0, així si tindràs Direct Rendering per l'aplicació en qüestió.

---

### Post by montagú on 2007-10-23
Solucionat!!!

He fet un 

```
apt-get remove --purge xserver-xorg
```

I despres a Synaptic he buscat tot ho relacionat amb "xserver" i "xorg" i he instal·lat el que creia convenient (pura intuició) i ja em funciona Compiz i l'AWN :D

Gracies!

---

