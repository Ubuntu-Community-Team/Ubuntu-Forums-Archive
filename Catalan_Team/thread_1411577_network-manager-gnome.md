---
title: "network-manager-gnome"
date: 2010-02-20
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2010-02-20
Bon dia.
A un Kubuntu li he insta&#320;lat el network manager de gnome.
En intentar iniciar-lo amb terminal fent: nm-applet
hem surt el següent:
request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

Googlejant una mica, he editat sense exit etc/network/interfaces

algú sap com puc inicar-lo, sisplau.
Gracies.

---

### Post by papapep on 2010-02-20
> Could not acquire the NetworkManagerUserSettings service **as it is already taken**

T'està dient que **ja** s'està executant.

Afegeix l'applet a la barra de tasques amb el procediment que Kde tingui (i jo no conec). Potser no tens l'applet de notificacions a la barra?

---

### Post by Miquel Ubuntero on 2010-02-22
gracies per respondre Papapep.
He afegit l'applet (nm-applet), pero res. continua sortint el mateix missatge.
També he provat: amb l'assistent de serveis KDE he aturat 2 serveis que he vist de xarxa, però tampoc a solventat res.
Seguiré googlejant, a veure que veig.
Salut i gracies.

---

### Post by papapep on 2010-02-22
> També he provat: amb l'assistent de serveis KDE he aturat 2 serveis que he vist de xarxa, però tampoc a solventat res.

Cal que expliquis amb més detall el que has fet, posant la ordre en concret, quins serveis has matat, etc. Si no, no podem saber si el que fas és correcte o si t'equivoques a algun punt i et podem ajudar.

---

### Post by wgarcia on 2010-02-22
Potser hagis d'aturar el knetworkmanager si estàs en KDE abans d'inicar el networkmanager:

sudo killall knetworkmanager

o 

sudo service knetworkmanager stop

---

### Post by Miquel Ubuntero on 2010-02-26
Gracies per respondre.
Ara estic ocupat en una altre avaria.
A veure si aquest cap de setmana miro aquesta i us dic com a anat.
Salut!

---

### Post by Miquel Ubuntero on 2010-02-27
Hola de nou.
Bé, una mica estrany, però ara ja hem funciona el nm-applet.
Quan dic funciona, vui dir que tinc accés a internet. Però no s'inicia automàticament la icona del network-manager per triar xarxes. Tot hi que al apartat de configuració de programes d'inici del KDE hi tinc possat el nm-applet.

De fet, si des de Terminal faig l'ordre nm-applet, si que disposo del gestor de xarxes gràfic. 

encara que no arrenqui automàticament, al menys ja hem funciona.

tot plegat una mica estrany.

En qualsevol cas, gràcies pel vostre interès.

Salut![COLOR="black"][/COLOR]

---

### Post by wgarcia on 2010-02-27
Suposo que sí que arrenca però no es mostra automàticament a KDE. Per això penso que has d'editar l'arxiu:

/etc/xdg/autostart/nm-applet.desktop 

i canviar la línia que posa:
OnlyShowIn=GNOME;XFCE;

per posar:
OnlyShowIn=GNOME;XFCE;KDE;

---

### Post by Miquel Ubuntero on 2010-02-27
SOLVED!!!
Bona garcia, molt bona so&#320;lució. Ara ja ho tinc i n'estic molt content.
Moltes gracies, de debò.
Ja feia uns quants dies que me'n sortia.
Salut!

---

