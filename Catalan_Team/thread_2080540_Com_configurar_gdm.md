---
title: "Com configurar gdm?"
date: 2012-11-04
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2012-11-04
bones.
Voldria saber si es pot "personalitzar" Gnome Display Manager amb Ubuntu 12.10
M'agradaria canviar la imatge de fons i alguna coseta més.
A molts llocs he llegit que es pot fer amb el gnome-control-center, cosa que no m'ha servit de res.
Gràcies.

---

### Post by jmaspons on 2012-11-06
Pots provar amb el lightdm, almenys pel KDE hi ha un modul als Arranjaments del sistema per modificar el què vols i suposo que la versió en GTK deu tenir algun equivalent. El paquet és lightdm-gtk-greeter

Salut!

---

### Post by wgarcia on 2012-11-06
Per a gdm just he vist un article sobre un programeta de configuració que té bona pinta:

[http://www.webupd8.org/2012/11/how-to-customize-gdm-36-login-lock.html](http://www.webupd8.org/2012/11/how-to-customize-gdm-36-login-lock.html)

---

### Post by Miquel Ubuntero on 2012-11-07
Hola amics.
referent a  lightdm-gtk-greeter, he de dir que no m'ha funcionat. si l'he pogut insta&#320;lar i, aparentment, es pot configurar una imatge de fons però no queda implementada a la pantalla de login.
He de dir que no sóc l'únic que li pasa, en altres foros hi ha més gent que es queixa del mateix.

Referent a l'enllaç que proposa wgarcia, el programet té bona pinta, però no està com a paquet, i això de compilar o quelcom semblant no és lo meu.
El que si m'ha servit d'inspiració és el comentari que fan en aquest enllaç amb refere&#505;cia a la carpete usr/share

Què he fet? Amb un Ubuntu 12.10 he cercat la imatge de fons de pantalla login a /usr/share/backgrounds i la he canviada per la que m'ha vingut de gust. això si que ha funcionat. Llàstima que encar no he trobat els "backgrounds" al Lubuntu 12.04.

Aprofito per comentar que, Ubuntu 12.10 utilitza Lightdm ([http://es.wikipedia.org/wiki/LightDM](http://es.wikipedia.org/wiki/LightDM)) com a utilitat de login; i versions més antigues, com per exemple Lubuntu 12.04, utilitzen gdm ([http://es.wikipedia.org/wiki/GNOME_Display_Manager](http://es.wikipedia.org/wiki/GNOME_Display_Manager)).

---

