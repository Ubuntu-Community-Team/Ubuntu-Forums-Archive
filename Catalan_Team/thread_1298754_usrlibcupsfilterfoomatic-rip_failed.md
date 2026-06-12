---
title: "/usr/lib/cups/filter/foomatic-rip failed"
date: 2009-10-23
forum: Catalan Team
---

### Post by jinglada on 2009-10-23
És molt dur per a mi seguir lluitant per a ser informàticament lliure, però també ho és en la resta de la vida i per això no em rendeixo, encara que de vegades estigui força desesperat com ara.

No ho he mesurat, però tinc la sensació que em passo més d'una tercera part del temps dedicat a l'ordinador intentant solucionar problemes.

Ja no puc tornar a imprimir sota Ubuntu jaunty.

Diu que ja ha acabat la impressió i el treball resta a la cua d'impressió aturat i a les propietats/configuració diu 'estat de la impressora: inactiva -/usr/lib/cups/filter/foomatic-rip failed'

Al cap d'una estona s'imprimeix el següent missatge:

*** Unable to open the initia device, quitting.

En el terminal passo 'hp-check -t' i sembla que tot estigui correcte, oi?

...
Checking for CUPS...
Status: scheduler is running
Version: 1.3.9
error_log is set to level: debug
....
------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

totes posa 'OK found'
...
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                           Model                          
  ---------------------------------------------------  -------------------------------
  hp:/usb/Officejet_6200_series?serial=CN5BMEG3970453  HP Officejet 6200 series       

...
---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

Officejet-6200-series
---------------------
Type: Printer
Device URI: hp:/usb/Officejet_6200_series?serial=CN5BMEG3970453
PPD: /etc/cups/ppd/Officejet-6200-series.ppd
PPD Description: HP Officejet 6200 series Foomatic/hpijs, hpijs 2.8.7
Printer /usr/lib/cups/filter/foomatic-rip failed idle.  enabled since dv 23 oct 2009 11:40:22 CEST
Communication status: Good

Officejet-6200-series_fax
-------------------------
Type: Fax
Device URI: hpfax:/usb/Officejet_6200_series?serial=CN5BMEG3970453
PPD: /etc/cups/ppd/Officejet-6200-series_fax.ppd
PPD Description: HP Fax
Printer Unplugged or turned offet-6200-series_fax disabled since dc 16 set 2009 12:52:17 CEST -
Communication status: Good

---------------
| USER GROUPS |
---------------

joan adm dialout cdrom plugdev lpadmin admin sambashare

----------------------------------
en un forum de Debian ([http://www.esdebian.org/foro/17574/solucionado-foomatic-rip-cerrado-status-1-problemas-cups-hp-deskjet-710c](http://www.esdebian.org/foro/17574/solucionado-foomatic-rip-cerrado-status-1-problemas-cups-hp-deskjet-710c))
he trobat això:
Basta con instalar pnm2ppa:
# apt-get install pnm2ppa
y se soluciona todo, era esa pequeña tontería.
-----------------------------------
Com que no sabia que era he fet
~$ whatis pnm2ppa
pnm2ppa (1)          - convert portable anymap (PNM) images to HP's PPA printer format.
~$ whereis pnm2ppa
pnm2ppa: /usr/bin/pnm2ppa /etc/pnm2ppa.conf /usr/share/pnm2ppa /usr/share/man/man1/pnm2ppa.1.gz
------------------------------------

Ja no sé que fer. Em podeu ajudar, sisplau?!

---

### Post by papapep on 2009-10-23
jinglada, [aquí]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/404122"), més concretament al [comentari núm. 2]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/404122/comments/2"), sembla que tinguin el mateix problema i diuen que ho han resolt.

---

### Post by jinglada on 2009-10-23
> **papapep said:**
> jinglada, [aquí]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/404122"), més concretament al [comentari núm. 2]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/404122/comments/2"), sembla que tinguin el mateix problema i diuen que ho han resolt.

Un milió de gràcies papapep. Seguint l'enllaç he cercat el hplip-3.9.6b.run al google i he trobat [http://ubuntuforums.org/showthread.php?t=1207881&highlight=HP+P1005](http://ubuntuforums.org/showthread.php?t=1207881&highlight=HP+P1005) on també justament el segon comentari diu que desinstal·lant i reinstal·lant ho va solucionar. Així ho he fet i ja torna a funcionar.

Allò trist és que havia imprès coses abans d'una típica actualització de les que gairebé a diari et proposa el gestor d'actualitzacions. No sé si és això però sovint em passa que coses que funcionen després de l'actualització s'espatllen.

Ah! i no em digueu que no sóc resistent. Puc ser inexpert i potser força inútil per al programari lliure però des d'ahir a la tarda que havia d'imprimir un full de càlcul i al final ho fet sota windows just abans de la resposta de papapep. Llàstima no haver resistit uns minutets més!!!:evil:

---

### Post by SiscoGarcia on 2009-10-24
No pateixis jinglada, aquest és el camí ;)

Jo també m'hi he trobat com tu, i ara tinc el problema (:P) que no podria fer-ho sota windows ni que vulgués... ja no el tinc (ni instal·lat ni de cap altra manera)... és l'evolució ;)

---

