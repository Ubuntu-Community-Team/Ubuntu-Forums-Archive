---
title: "Connexió Banda ample mòbil movistar jaunty"
date: 2009-07-29
forum: Catalan Team
---

### Post by ilku on 2009-07-29
Hola Companys
He adquirit una connexió de banda ample mòbil de movistar. He aconseguit que funcioni, però sempre he de fer al terminal un eject /dev/sr0 ja que s'autoexecuta com un cd i fins que no es desmonta aquesta unitat de cd no hi ha manera que funcioni.
Sabeu d'alguna manera perque no hagi de fer aquest pas, ja que el mòdem no és per mi, sino per un usuari (no gaire destre).
En principi a falta d'una solució millor he fet un llançador al escriptori que executa aquesta ordre "eject /dev/sr0", d'aquesta manera ja troba el mòdem i pot connectar-se.
Es un novatel, utilitzo jaunty, l'he configurat a partir del networkmanager (sense cap problema, tot s'ha de dir).

Gracies per tot

PD. no m'explico gaire bé si alguna cosa no s'entén provaré de resoldre el dubte.

---

### Post by PatrickVogeli on 2009-07-29
mm segurament es podria fer una regla d'udev per al dispositiu en questió.. pero no sabria ben be que posar-hi.

salut

---

### Post by oriolsbd on 2009-07-29
També em sona que hi havia alguna opció per posar al fitxer fstab on li deies que no et muntés el dispositiu. Ara mateix no la trobo. A algú més li sona?

Salut!

---

### Post by orestesmas on 2009-07-30
> **ilku said:**
> Hola Companys
He adquirit una connexió de banda ample mòbil de movistar. He aconseguit que funcioni, però sempre he de fer al terminal un eject /dev/sr0 ja que s'autoexecuta com un cd i fins que no es desmonta aquesta unitat de cd no hi ha manera que funcioni.
Sabeu d'alguna manera perque no hagi de fer aquest pas, ja que el mòdem no és per mi, sino per un usuari (no gaire destre).


Intueixo que el comportament és similar al d'un Alcatel X060, per la qual cosa el teu programa (fins que els d'Ubuntu no incorporin de sèrie alguna cosa millor) és el USB_modeswitch. Tot el procediment [està explicat aquí]("http://orestes.caliu.cat/2009/07/06/lluitant-amb-un-modem-alcatel-x060-de-simyo-part-1/"). Encara que està descrit per un Alcatel X060, es pot adaptar per aquests Novatel:

# Novatel Wireless Ovation MC950D HSUPA
# Novatel Wireless Merlin XU950D
# Novatel Wireless Ovation 930D
# Novatel U727 USB modem
# Novatel MC990D
# Novatel U760 USB modem

simplement descomentant les línies pertinents del fitxer de configuració.

Espero que et serveixi

---

### Post by ilku on 2009-07-30
tens rao ja funciona, de totes maneres he vist que ara és mes fàcil encara.

1.-Descarregar el .deb [http://www.draisberghof.de/usb_modeswitch/#automate]("http://www.draisberghof.de/usb_modeswitch/#automate")
2.-L'instal·les amb el gdebi
3.-Configures el usb_modeswitch per al teu dispositiu situat a #/etc/
4.-Configures la teva connexió amb el networkmanager i a treballar :D.

Nota: he trobat 2 llocs a part del apuntat abans per l'Orestes
[http://diegosamuel.blogspot.com/]("http://diegosamuel.blogspot.com/")
[http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html]("http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html")

Gracies a tots

---

