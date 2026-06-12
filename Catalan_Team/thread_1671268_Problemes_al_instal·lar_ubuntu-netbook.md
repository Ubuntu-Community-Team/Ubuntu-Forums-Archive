---
title: "Problemes al instal·lar ubuntu-netbook"
date: 2011-01-19
forum: Catalan Team
---

### Post by open-pitu on 2011-01-19
Bones!

Ja fa dies que tinc ganes de provar el nou entorn d'escriptori que incorporarà Ubuntu en la propera versió. Per a fer-ho, tenint Ubuntu 10.04, cal instal·lar el paquet ubuntu-netbook.

Quan executo l'apt-get tot fa bona pinta exceptuant que vol baixar paquets relacionats amb l'OpenOffice, ja que ja fa un temps (de seguida que vaig poder) em vaig passar a LibreOffice.

De manera que salta aquest error:

[INDENT]```
S'està desempaquetant openoffice.org-common (de .../openoffice.org-common_1%3a3.2.0-7ubuntu4.1_all.deb) ...
dpkg: s'ha produït un error en processar /var/cache/apt/archives/openoffice.org-common_1%3a3.2.0-7ubuntu4.1_all.deb (--unpack):
 s'està intentant sobreescriure «/usr/bin/ooffice», que també està en el paquet libreoffice-common 1:3.3.0~rc2-3lucid1
S'han trobat errors en processar:
 /var/cache/apt/archives/openoffice.org-common_1%3a3.2.0-7ubuntu4.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```[/INDENT]

No sé si algú més si ha trobat, o si el què es pot fer és evitar que intenti instal·lar aquest paquet...

Espero les vostres respostes!

---

### Post by wgarcia on 2011-01-20
Em sembla que el paquet es diu únicament "unity" i no "ubuntu-netbook", per tant hauries de fer

sudo apt-get install unity

i en entrar et donarà opció d'escollir entre la sessió normal o unity. 


Potser millor per provar-ho és crear-se una màquina virtual i instal·lar l'alpha de 11.04, perquè s'estan introduint molts canvis respecte al que hi ha ara als netbooks.

---

### Post by kimet on 2011-01-20
LibreOffice es un fork d'OpenOffice, sembla alguns paquets estan anomenats igual i apt-get, al intentar resoldre dependències es troba amb algun conflicte. 
Prova a retenir OpenOffice o el paquet que crea conflictes.
(hauries de tenir en compte que libreoffice està en experimental ;))

---

### Post by open-pitu on 2011-01-20
wgarcia: EL de Unity és per a la 10.10, per a la 10.04 és ubuntu-netbook. Tot i així també ho he provat amb unity i dóna els mateixos problemes. En un altre PC tinc intenció d'instal·lar-hi la versió 11.04 per veure què tal, però em faria gràcia veure en el portàtil si em pot anar bé, ja que properament hi haurà una "lluita" entre Unity i Gnome3.

kimet: com es configura per a que no instal·li aquest paquet d'OO common?

Moltes gràcies als dos! Algú ha provat el nou entorn d'escriptori?

---

### Post by wgarcia on 2011-01-20
Em sembla que Unity es va introduir per primer cop a la 10.10.

Perquè no actualitzi openoffice la instrucció pot ser

sudo "echo openoffice hold" | dpkg --set-selections

però no sé si no continuaràs tenint problemes de conflicte de dependències entre l'openoffice i el libreoffice. 

En quant al conflicte crec que serà entre gnome-shell i unity, i no entre gnome3 i unity perquè unity no deixa d'estar construït sobre gnome3. Una altra cosa que he observat que és que hi ha una mena de convergència entre gnome-shell i unity, moltes coses de gnome-shell s'estan semblant a algunes coses que fa unity. 

No l'he provat a les versions alpha de la natty (sí a un netbook amb 10.10 però està evolucionant molt), però si vols veure algun vídeo el pots trobar per exemple a:

[http://www.webupd8.org/2011/01/unity-3d-gets-new-experimental-options.html](http://www.webupd8.org/2011/01/unity-3d-gets-new-experimental-options.html)

---

### Post by wgarcia on 2011-01-20
Em sembla que Unity es va introduir per primer cop a la 10.10.

Perquè no actualitzi openoffice la instrucció pot ser

sudo "echo openoffice hold" | dpkg --set-selections

però no sé si no continuaràs tenint problemes de conflicte de dependències entre l'openoffice i el libreoffice. 

En quant al conflicte crec que serà entre gnome-shell i unity, i no entre gnome3 i unity perquè unity no deixa d'estar construït sobre gnome3. Una altra cosa que he observat que és que hi ha una mena de convergència entre gnome-shell i unity, moltes coses de gnome-shell s'estan semblant a algunes coses que fa unity. 

No l'he provat a les versions alpha de la natty (sí a un netbook amb 10.10 però està evolucionant molt), però si vols veure algun vídeo el pots trobar per exemple a:

[http://www.webupd8.org/2011/01/unity-3d-gets-new-experimental-options.html](http://www.webupd8.org/2011/01/unity-3d-gets-new-experimental-options.html)

---

### Post by kimet on 2011-01-20
> kimet: com es configura per a que no instal·li aquest paquet d'OO common?
 
Si uses synaptic localitzes el paquet i al menu de dalt selecciones *paquet* i *bloca la versió.*

Si aptitude: aptitude hold paquet.

---

### Post by open-pitu on 2011-01-20
Bones amb les pistes que m'heu donat he conseguit alguns avanços. Puntualitzo que teníeu raó, que cal el paquet unity, però aquest no el trobo per a la 10.04.

El què he fet és:

[INDENT]```

$ sudo aptitude hold openoffice.org-common
$ sudo aptitude hold openoffice.org-common
$ sudo aptitude install ubuntu-netbook

```[/INDENT]

Amb això he conseguit tenir la versió netbook, amb les seves limitacions, sobretot la de no poder modificar el menú principal. Navegant he trobat aquest [link]("http://caymcorp.wordpress.com/2010/05/05/anadir-applets-al-panel-de-ubuntu-netbook-edition-10-04/") que es resumeix en:

[INDENT]```

$ sudo ln -s /etc/xdg/xdg-une/autostart/maximus-autostart.desktop /etc/xdg/autostart/
$ sudo ln -s /etc/xdg/xdg-une/autostart/maximus-autostart.desktop /etc/xdg/autostart/
$ sudo ln -s /etc/xdg/xdg-une/autostart/netbook-launcher.desktop /etc/xdg/autostart/
$ sudo ln -s /usr/share/gconf/une/default/20_une-gconf-default /usr/share/gconf/defaults/
$ sudo ln -s /usr/share/gconf/une/mandatory/20_une-gconf-mandatory /usr/share/gconf/defaults/
$ sudo update-gconf-defaults

```[/INDENT]

I el resultat és que en la nostra antiga versió de Gnome podem posar-hi la interfície de l'altre entorn, podem modificar els applets.

El tema és, no aconseguiexo trobar el repositori on Ubuntu 10.04 pot instal·lar el paquet unity, per tal de provar l'entorn, i que en principi en la 10.10 és amb aquest paquet. Algú ho ha provat?

Moltes gràcies per les vostres respostes!!

---

### Post by wgarcia on 2011-01-21
En aquest enllaç

[http://digitizor.com/2010/05/10/how-to-install-unity-in-ubuntu-10-04-lucid-lynx/](http://digitizor.com/2010/05/10/how-to-install-unity-in-ubuntu-10-04-lucid-lynx/)

dóna un PPA on sembla que hi ha el unity per 10.04, però també hi ha una nota que diu ara no està funcionant.

---

### Post by open-pitu on 2011-01-24
I certament no troba el paquet Unity. He buscat molt per a la xarxa i no he conseguit trobar aquest paquet. Si algú el troba que comparteixi el repositori, jo així ho faré tant bon punt el trobi!

---

