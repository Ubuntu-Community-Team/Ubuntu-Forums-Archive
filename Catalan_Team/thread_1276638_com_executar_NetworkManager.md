---
title: "com executar NetworkManager"
date: 2009-09-27
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-09-27
bones.
Tinc un Xubuntu 9.04 que ocasionalment entro amb escriptori LXDE.
Voldria saber quant utilitzo LXDE com utilitzar NetworkManager per cercar wifis, donat que per defecte a LXDE no veig per enlloc la icona que Xubuntu te al costat del horari per cercar wifis.
Gracies.

---

### Post by papapep on 2009-09-27
No tinc clar que l'LXDE acabi de funcionar a l'hora amb el nm. Instal·la el [Wicd]("http://packages.ubuntu.com/search?keywords=wicd&searchon=names&suite=jaunty&section=all") i t'anirà perfecte.

---

### Post by Miquel Ubuntero on 2009-09-27
D'acord. Ja el conec.
Saps si el puc insta&#320;lar sense internet? Amb cd o quelcom?
Gracies.

---

### Post by papapep on 2009-09-27
És al repositori Universe, o sigui que no ve als CD. El pots descarregar amb un altre ordinador i passar el fitxer amb una clau usb. Vigila les dependències que ja les tinguis a l'ordinador destí. Són els paquets que tenen una bola vermella a l'esquerra: [http://packages.ubuntu.com/jaunty/wicd](http://packages.ubuntu.com/jaunty/wicd)

---

### Post by Tomàs M. on 2009-09-27
Si no recordo malament, l'altre dia el vaig executar a LXDE amb
$ nm-applet
i em va funcionar...
Salut!

---

### Post by papapep on 2009-09-28
> Si no recordo malament, l'altre dia el vaig executar a LXDE amb
$ nm-applet
i em va funcionar...

L'únic "problema" de fer anar el Network Manager amb algun entorn d'escriptori que no sigui Gnome és la carretada de dependències que té i que instal·laràs només pel nm. Amb el Wicd, això t'ho estalvies.

---

### Post by Miquel Ubuntero on 2009-09-28
Gracies a tots dos.
De moment donat que a la màquina amb LXDE també tinc Gnome, he preferit utilitzar network manager. Fen correr la comanda nm-applet m'ha anat be.
Gracies de nou.
Salut!

P.D.: Està prou be al LXDE, papapep. el seguiré provant.

---

