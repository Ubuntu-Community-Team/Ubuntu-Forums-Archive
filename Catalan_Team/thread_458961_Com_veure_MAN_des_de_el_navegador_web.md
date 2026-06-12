---
title: "Com veure MAN des de el navegador web"
date: 2007-05-30
forum: Catalan Team
---

### Post by prostata on 2007-05-30
Degut a la qüestió sobre formatr diskettes, que va sorgir la sentencia man, us envio per si és del vostre interès, com fer per poder visualitzar en el vostre navegador web, tot el contingut de la sentencia man de forma mès àgil que per la consola, o al menys és per a mi força més interesant, es com si fos tenri el manual complert a la mateixa ma.

heu de fer:

A)      sudo apt-get install apache2 man2html

B)      cap al final del proces tindreu una lìnia semblan a aquesta:

          [http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html) (*)

(*)      però amb el vostre nomb d'usuario-desktop, en el meu cas com a exemple:           [http://josep-desktop/cgi-bin/man/man2html](http://josep-desktop/cgi-bin/man/man2html)

C)      obriu el navegador i poseu aquesta direcció per cercar i veureu que bé que va. Evidentment i per tal de poder accedir sempre que volgueu, haureru de guardar questa pàgina.

Espero que us sigui útil

Salut

---

### Post by orestesmas on 2007-05-30
Bé, de fet la cosa és encara més simple si uses kubuntu: només cal obrir el Konqueror i teclejar la URL

**man:nom_de_l'aplicació**

I hopla! ja ho tens...

El konqueror és ple d'aquestes sorpreses. Són els "kioslaves", i n'hi ha un munt.

---

### Post by papapep on 2007-05-31
A Gnome (sí, Orestes, hi ha vida després de KDE!! ;)) si crides l'epiphany (el navegador de Gnome) i hi fiques també, per ex., "man:aptitude" també et mostra la pàgina man que has demanat.

---

### Post by orestesmas on 2007-05-31
No fotis! Han aconseguit programar-ho? I usant només C a pèl? Ostres, això sí que són mascles de pèl en pit....

:-P

---

### Post by crazyserver on 2007-05-31
I fins i tot al firefox! brutal! tot s'ha de dir que obre una finestra amb el gnome help...;)

---

