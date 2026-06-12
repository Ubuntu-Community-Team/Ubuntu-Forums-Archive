---
title: "gnome-bluetooth"
date: 2010-03-09
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2010-03-09
Bones.
Al meu Kubuntu he insta&#320;lat el paquet del bluetooth de gnome.
El que hem passa és que no se com iniciar-ho. No surt en cap menú del kde i no se com fer-ho des de terminal.
algú sap quina ordre emprar des de terminal?
gracies.

---

### Post by MiquelBLL on 2010-03-10
No faig servir KDE pero suposo que Editan els Menus  i seleccionan el del bluetooth perque es vegi ja funcionaria, o tambe posan el nom correcte al terminal.

---

### Post by akyra on 2010-03-10
Consulta aquesta web, a mi em funciona perfectament:
[http://www.alexxoid.com/blog/linux/how-to-enable-bluetooth-on-toshiba-satellite-a300-laptop.html]("http://www.alexxoid.com/blog/linux/how-to-enable-bluetooth-on-toshiba-satellite-a300-laptop.html")

Per rebre fitxes en el PC també he fet servir això:
hcitool dev
obexpushd hci0

Extret de la web: [http://nuestrasfrikadas.blogspot.com/2009/11/como-recibir-archivos-por-bluetooth-en.html]("http://nuestrasfrikadas.blogspot.com/2009/11/como-recibir-archivos-por-bluetooth-en.html")

Diguem si et va bé.

Salutacions

---

### Post by Miquel Ubuntero on 2010-03-11
Bones.
Tal com comenta MiquelBLL, el que hem cal és l'ordre correcta al terminal per poder executar el gnome-bluetooth.
Aquest programa va perfecte amb el meu mòbil des d'Ubuntu.
El que voldria és poder utilitzar-lo des de Kubuntu.
Però per més que googlejo, no dono amb l'ordre que necessito.
Gràcies pel vostre interès.

---

### Post by CarlesOriol on 2010-03-11
No sé si funciona amb kde... però el paquet blueman és espectacular

---

### Post by akyra on 2010-03-12
El que et refereixes podria ser l'ordre: bluetooth-applet

Ja diràs

---

### Post by Miquel Ubuntero on 2010-03-12
Hola.
Si executo bluetooth-applet, tinc el següent error:
miquel66@ladtopmiquel:~$ bluetooth-applet
** Message: adding killswitch idx 1 state 1
** Message: adding killswitch idx 4 state 1
** Message: Reading of RFKILL events failed
** Message: killswitch 1 is 1
** Message: killswitch 4 is 1
** Message: killswitches state 1
** (bluetooth-applet:2387): DEBUG: Unhandled UUID 00005001-0000-1000-8000-0002ee000001 (0x5001)
** (bluetooth-applet:2387): DEBUG: Unhandled UUID 00005002-0000-1000-8000-0002ee000001 (0x5002)
** (bluetooth-applet:2387): DEBUG: Unhandled UUID 00005003-0000-1000-8000-0002ee000001 (0x5003)
** (bluetooth-applet:2387): DEBUG: Unhandled UUID 00005601-0000-1000-8000-0002ee000001 (0x5601)
** Message: killswitch 1 is 1
** Message: killswitch 4 is 1
** Message: killswitches state 1

(bluetooth-applet:2387): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: S'ha produït un error en obrir el directori «/usr/share/gvfs/remote-volume-monitors»: No such file or directory


Per altra banda, he insta&#320;lat el paquet blueman i tinc el mateix problema que amb bluetooth-gnome, que no puc iniciar-lo. No veig cap acces des de el menu de programes i no sé com iniciar-lo des de terminal.
Carles, saps com iniciar-lo amb terminal?

MOltes gracies a tots dos.

---

### Post by CarlesOriol on 2010-03-12
blueman-applet

---

### Post by Miquel Ubuntero on 2010-03-12
Hola.
Anem a pams.

El blueman. He aconseguit iniciar-ho. Puc enviar arxius del pc al mòbil, però no al inreves. i el mòbil simplement diu que no pot. Sense maxa explicacions.

gnome-bluetooth. Mirant una mica l'error que hem donava, he vist que deia que mancava un directori, el remote...
Aleshores, he creat manualment aquest directori, poden iniciar gnome-bluetooth. Aquí hem passa el mateix que amb blueman. pc a mòbil sí.
Mòbil a pc no.

LLavors, amb gnome-bluetooth, he intentat l'opció "navega pels fitxers del sipositiu". Que aquesta si hem funciona des de Ubuntu. Però sorprenentment, amb Kde, no. Diu això:
"El Nautilus no pot gestionar ubicacions «obex»"

Continuaré googlejant.
Ja us diré.

---

### Post by Miquel Ubuntero on 2010-03-13
Hola de nou.
Fent noves proves amb el meu mòbil, que és nou. M'he donat conte que tampoc transfereix arxius amb bluetooth cap un altre mòbil. Crec que passaré per la botiga per què hem fa l'efecte que no va bé.

en qualsevol cas, amb el cable usb que porta, si que he pogut transferir arxius al pc i al inrevés. Que és el que hem calia en aquests moments.

Bé, sempre hi ha una alternativa.
Salut, i gràcies a tots.

---

### Post by jmfubu on 2011-05-08
Tinc ubuntu 11.04 en un portàtil. Tinc bluetooth usb. L'ordinador el detecta però em surt que està inhabilitat (amb una creu). Si miro preferències puc clicar "engega el bluetooth" però continua inhabilitat. Què puc fer?
 
Gràcies.

---

### Post by wgarcia on 2011-05-11
Convindria que obrissis un fil nou. El fil que has reutilitzat té més d'un any i sembla un problema diferent al teu (tot i que relacionat amb el bluetooth també).

---

