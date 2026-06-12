---
title: "es queda carregant"
date: 2010-09-26
forum: Catalan Team
---

### Post by Haliotis on 2010-09-26
Hoal família.
ja fa quasi un parell d'anys que estic amb ubuntu. Ara estic amb la versió 10.4 en un dell inspiron.
aquests darrers mesos he estat bastant ocupat amb el projecte de tesina, i no he tingut gaire cura de l'ubuntu... tot i així, quan automàticament em deia d'actualitzar, ho feia i llestos...
a la facultat vam tenir algun problema amb el wifi, ha vegades es tallava, o anava molt lent...
així que la setmana passada tenia alguna actualització que no s'havia pogut acabar, pel que es veu. Des de casa (sense problemes amb el wifi) vaig actualitzar tot el que vaig poder, però també em va donar algun error. Com que em quedava un dia per presentar la tesina, no li vaig donar importància esperant posar-m'hi seriosament, un cop defensada. La sorpresa va ser que l'ubuntu no se m'ha tornat a engegar. Quan surt el grub, trio l'ubuntu normal, i es queda carregant el logo d'buntu, amb una definició de pantalla més baixa de lo habitual i es pot passar hores així (bé nomé she comprovat que aguanta mitja hora carregant).
Sé que dono poca informació... però necessito una ajudeta per començar a mirar com us puc donar més informació.
Gràcies per tot

---

### Post by kukat on 2010-09-26
Pots provar d'iniciar la consola de recuperació al Grub, i així veiem si és alguna cosa de l'entorn gràfic. 
Una vegada iniciada (si inicia....) pots provar:

sudo /etc/init.d/gdm start (per a GNOME)
sudo /etc/init.d/kdm start (per a KDE)


a veure que passa....

salut

---

### Post by Haliotis on 2010-09-26
Ok
des del grub he entrat al mode de reestabliment...
ha tardat una estona, i al final de les línies que semblaven coherents es llegia:
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
(initramfs)

Llavors he escrit seguit a la última línia:
(initramfs) sudo /etc/init.d/gdm start

i m'ha respost:
/bin/sh: sudo: not found
(initramfs)

no sé, des d'aquí puc moure'm per carpetes, faig un ls i em surten les carpetes que hi ha al sistema d'arxius... no estic segur si apareixen totes... de fet, home no hi és. (home està en una altra partició de disc, no sé si te a veure).

En fi, qualsevol interpretació, serà benvinguda, i qualsevol consell nou, per anar provant també.
gràcies!

---

### Post by kukat on 2010-09-27
Pots extraure alguna línia d'aquestes "no-coherents" per veure si ens diuen alguna cosa???

Tens altre Sistema Operatiu Insta&#320;lat, i funciona correctament? (per descartar problemes de maquinari...)

De totes formes, pots posar-nos el que et trau la següent comanda?

tail /var/log/syslog

Et sortiran 10 línies. pots ficar-ho a dins d'un fitxer amb:

tail /var/log/syslog >> resultat.txt 

i copiar-lo al pendrive, per exemple. 

Però si no veus la partició de la /home, pot ser tingues un problema amb el maquinari.....
Bé, poden ser moltes coses, de moment mirem el syslog! 
;)

---

### Post by Haliotis on 2010-09-27
Començo a patir que no sigui molt més complicat del que em pensava...
no existeix cap carpeta log/ dins de var/
la única carpeta que hi ha és lock/, i no conté cap arxiu syslog
> Pots extraure alguna línia d'aquestes "no-coherents" per veure si ens diuen alguna cosa???
aquí escric les 5 línies que hi ha sobre el que ja vaig escriure en l'atre missatge:
[     6.561119] sd 7:0:0:0: [sdc] Write protect is off
[     6.570365] sd 7:0:0:0: [sdc] Assuming drive cache: write enough
[     6.590450]sdc: sdc1
[     6.603119] sd 7:0:0:0: [sdc] Assuming drive cache: write enough
[     6.612236] sd 7:0:0:0: [sdc] Attached SCSI removable disk

> Tens altre Sistema Operatiu Insta&#320;lat, i funciona correctament? (per descartar problemes de maquinari...)
Sí, també hi ha el vista, que é samb el que vaig tirant i vaig escrivint al fòrum (però molt que em pesi :( )
O sigui que descartaria problema de hardware... tot i que tb és veritat que tot plegat va passar entre apagar el portatil al matí a casa, i encendre'l una hora més tard a la facultat (viatge en metro, escales i tal) A veure, no faig el boig amb la motxilla... però vaja... Windows funciona com sempre (és horrorós, però no fa res fora de l'habitual).
Gràcies pels esforços

---

### Post by wgarcia on 2010-09-27
Prova arrencar amb un LIVE CD, a veure si pots veure les particions que tenies muntades (/home) etc., i aprofita per salvar totes les dades que et siguin importants abans de continuar.

---

