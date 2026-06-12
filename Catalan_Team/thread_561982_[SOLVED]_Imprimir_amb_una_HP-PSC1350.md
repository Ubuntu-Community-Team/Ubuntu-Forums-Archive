---
title: "[SOLVED] Imprimir amb una HP-PSC1350"
date: 2007-09-28
forum: Catalan Team
---

### Post by Asus4 on 2007-09-28
Salut!

És el primer cop que escric en aquest blog, però fa temps que m'hi passo com a visitant ja que fa relativament poc que vaig passar-me a Ubuntu.

Tinc la versió Feisty Dawn, i vaig voler conectar-hi una impressora HP PSC-1350. Seguint un tutorial en un altre forum ([aquest]("https://help.ubuntu.com/community/HpAllInOne")) vaig fer la instal·lació i, un cop reiniciat l'escriptori i fet els passos adequats de reconeixement de la impressora (Sistema/Impressió...) vaig obrir l'OpenOffice per imprimir un document i va funcionar sense cap problema. Vaig poder imprimir unes quantes pàgines.

El problema va arribar al cap d'una estona d'estar imprimint. La impressora rebia l'ordre, començava a imprimir i de cop es parava a mitja impressió.
Com que feia molta estona que estava imprimint vaig deixar-ho estar i, aquest matí m'hi he tornat a posar i m'ha tornat a passar el mateix. Sigui el document que sigui, la impressora s'atura a mitja impressió.

El que més m'estranya de tot plegat és que al principi va funcionar correctament. 
De tota manera, el tutorial que vaig fer servir, no incloïa el model 1350 entre els models d'impressores suportats pel paquet ***hpoj***, però el mateix autor del manual ja anunciava que aquest era un model bastant proper al 1310 i que per tant, hauria de funcionar.


Algú sap quin motiu pot tenir la impressora per deixar d'imprimir sense motiu?
Gràcies!!!:)

---

### Post by papapep on 2007-09-28
Aquí:

[http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1350](http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1350)

Diu que t'hauria de funcionar perfectament. Però especifica que el paquet ha de ser el HPLIP, el qual es troba als repositoris d'Ubuntu.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=names&subword=1&version=feisty&release=all)

Jo provaria amb l'HPLIP a veure com et va. Així podràs veure si és cosa del controlador i començar a delimitar el problema.

Per cert, benvingut a la comunitat!

---

### Post by Asus4 on 2007-09-28
Primer de tot gràcies per contestar i donar-me la benvinguda!!

Referent al tema de la impressora, m'he mirat això del HPLIP i la distribució d'Ubuntu Feisty Dawn ja porta per defecte aquest paquet, però de totes maneres he borrat la impressora i he tornat a fer els passos que havia fet. 
Un cop instalada de nou, la impressora m'ha imprès dos fulls, però al tercer ja m'ha tornat a passar el mateix que abans.

Com que en tutorial que he fet servir ho posava, he anat en una consola i he escrit *hp-setup* i això és el que m'ha sortit:

joan@joan-desktop:~$ hp-setup

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
error: PyQt init failed. Reverting to interactive mode.
error: You must be root to run this utility.
joan@joan-desktop:~$ 

----

Aquests tres errors no els entenc i per tant tampoc sé si poden ser la font dels errors de la impressora. 
Atentament,

---

### Post by pespin on 2007-09-28
> error: You must be root to run this utility.
Aquest es ben clar, et diu que has d'executar el programa (ht-setup) amb permisos de root.
```

sudo hp-setup
```

---

### Post by Asus4 on 2007-09-29
Gràcies pespin! He mirat aquest error i era ben evident si..hehe
De tota manera, havent solucionat aquest, encara en tinc dos mes. Com que no entenc el que em surt a la consola, quan teclejo *sudo hp-setup* us ho passo per a veure si em podeu ajudar.
Perdoneu per ser tant pesat! Però no sé què passa...problemes de principiant^^?

> 
joan@joan-desktop:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
error: PyQt init failed. Reverting to interactive mode.
Using device: hp:/usb/psc_1300_series?serial=HU3951Q1KN9F

Setting up device: hp:/usb/psc_1300_series?serial=HU3951Q1KN9F

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)

warning: Cannot setup fax - device does not have fax feature.

PRINT QUEUE SETUP

Please enter a name for this print queue (m=use model name:'psc_1300'*, q=quit) ?m
Using queue name: psc_1300

Found a possible PPD file: foomatic:HP-PSC_1300-hpijs.ppd
Desc: HP PSC 1300 Foomatic/hpijs (recommended)

Note: The model number may vary slightly from the actual model number on the device.

Does this PPD file appear to be the correct one (y=yes*, n=no, q=quit) ?y
Enter a location description for this printer (q=quit) ?q
OK, done.




Gràcies!:)

---

### Post by papapep on 2007-09-29
Crec que et falta el paquet pyqt-tools:

```
sudo aptitude update
```

i quan acabi:

```
sudo aptitude install pyqt-tools
```

---

### Post by pespin on 2007-09-29
```
error: PyQt not installed. GUI not available. Exiting.
```

Segurament et falta el paquet PyQT, que és la interface gràfica Qt per a python.

Prova amb:
```

sudo aptitude install python-qt4
```

---

### Post by Asus4 on 2007-09-29
Operació feta: s'ha instal·lat correctament.
Però els errors continuen apareixent.

He anat al synaptic i he vist que hi ha molts paquets que porten per nom Phyton-Qt, però no els sé diferenciar, no sé si n'hi ha algun que hauria de tenir instal·lat o no...

[Això]("http://img241.imageshack.us/img241/6331/capturasynapticmp4.jpg") és el que veig al Synaptic.

Això és el que veig a la consola:
> 
el nom dels
següents paquets conté "python-qt":
  python-qt3-gl-dbg python-qt4-sql-dbg python-qtext python-qt3-dbg 
  python-qt3-doc python-qtext-dbg python-qt4-gl-dbg python-qt3-gl 
  python-qt3 python-qt4 python-qt4-gl python-qt4-dbg python-qt4-dev 
  python-qt4-doc python-qt-dev python-qt4-sql 


Merci!!

---

### Post by papapep on 2007-09-29
> Però els errors continuen apareixent.


I és **exactament igual** que abans??? Ens l'hauries de tornar a enganxar, si us plau.

---

### Post by pespin on 2007-09-29
Mm podria ser que utilitzés la versió qt3 i no la 4?

---

### Post by Asus4 on 2007-09-29
Surt **exactament el mateix**.
Ara he tornat a la terminal per poder-vos enganxar el que em surt, i al final m'ha acabat imprimint una pagina de prova.
He corregut a intentar imprimir un document de l'OpenOffice i m'ha tornat a passar el mateix que abans: es queda aturada a mitja impressió.

Us passo el que em surt integrament. Al final diu que vagi a provar a la pàgina si tinc problemes amb impressió.

> joan@joan-desktop:~$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
error: PyQt init failed. Reverting to interactive mode.
Using device: hp:/usb/psc_1300_series?serial=HU3951Q1KN9F

Setting up device: hp:/usb/psc_1300_series?serial=HU3951Q1KN9F

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)

warning: Cannot setup fax - device does not have fax feature.


PRINT QUEUE SETUP

Please enter a name for this print queue (m=use model name:'psc_1300'*, q=quit) ?
Using queue name: psc_1300

Found a possible PPD file: foomatic:HP-PSC_1300-hpijs.ppd
Desc: HP PSC 1300 Foomatic/hpijs (recommended)

Note: The model number may vary slightly from the actual model number on the device.

Does this PPD file appear to be the correct one (y=yes*, n=no, q=quit) ?
Enter a location description for this printer (q=quit) ?
Enter additonal information or notes for this printer (q=quit) ?

Adding print queue to CUPS:
Device URI: hp:/usb/psc_1300_series?serial=HU3951Q1KN9F
Queue name: psc_1300
PPD file: foomatic:HP-PSC_1300-hpijs.ppd
Location: 
Information: 
 

Would you like to print a test page (y=yes*, n=no, q=quit) ?

HP Linux Imaging and Printing System (ver. 1.7.3)
Testpage Print Utility ver. 4.1

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Printing test page to printer psc_1300...
Test page has been sent to printer. Waiting for printout to complete...
 
note: If an error occured, or the test page failed to print, refer to the HPLIP website
note: at: [http://hplip.sourceforge.net](http://hplip.sourceforge.net) for troubleshooting and support.

Done.
Done.


Tampoc he provat d'instal·lar el Qt3.
Si aquest és el problema, ho faré quan pugui!
Gràcies per la paciència!!

---

### Post by Asus4 on 2007-10-02
Al final m'he decidit i he instalat el Qt3 que en pespin m'ha recomanat.
He tornat a teclejar *sudo hp-setup* a la consola i m'ha tornat a instal·lar la impressora. He fet els passos i m'ha demanat d'imprimir una pàgina de prova, cosa a la qual he accedit i la impressora ha fet sense cap mena de problema.

Miraculosament (pel meu nivell d'Ubuntu és un miracle xD), seguidament, m'ha imprès dos documents d'OpenOffice sense quasi problemes. En el primer no s'ha queixat gens i en el segon s'ha anat parant una mica però anava seguin la impressió (una mica a batzegades). El fet és que de moment sembla que imprimeixi sense cap problema.

De tota manera, encara tinc dubtes sobre el perquè no funcionava?, què és Phyton i les versions Qt3 i Qt4? 

Per acabar vull agrair a tothom que m'ha ajudat a arreglar el problema!! 

Ens anem llegint pel fòrum!

---

### Post by papapep on 2007-10-02
Què és Python:

[http://ca.wikipedia.org/wiki/Python](http://ca.wikipedia.org/wiki/Python)

Què són les Qt:

[http://ca.wikipedia.org/wiki/Qt](http://ca.wikipedia.org/wiki/Qt)

Ambdós combinats són els que t'han presentat l'interfície gràfica per poder configurar l'impressora.

Aleshores, què passava que no et funcionava correctament la impressora? Doncs probablement que al no carregar-se l'interfície gràfica no acabava de fer algunes de les operacions necessaries per a configurar degudament el teu model de màquina. No se m'acudeix res més.

---

