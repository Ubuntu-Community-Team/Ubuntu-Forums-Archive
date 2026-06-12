---
title: "targeta gràfica ati radeon 9200 i ubuntu 12.04"
date: 2012-05-10
forum: Catalan Team
---

### Post by pinetell on 2012-05-10
Hola
Acabo d'actualitzar a l'ubuntu 12.04 i la targeta gràfica que fins ara em reconeixia ara no funciona.

Com que sóc molt novell amb aquestes coses, he demanat ajut i us puc donar força informació per ajudar a qui tingui alguna possible solució ja que en aquests moments qualsevol pel·lícula que miro és un passe de diapositives en que el a més, el so va per lliure. 

gràcies

**la targeta gràfica que tinc és:**

lspci -nn | grep VGA 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

**Les ordres que he seguit són les que surten al web:**

[http://www.upubuntu.com/2012/04/how-to-install-amd-ati-catalyst-124.html](http://www.upubuntu.com/2012/04/how-to-install-amd-ati-catalyst-124.html)

**I l'erro que em dóna és:**

Removing temporary directory: fglrx-install.hdlU0e
pep@pepubuntu:~/catalyst12.4$ more /usr/share/ati/fglrx-install.log
Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Dryrun uninstall succeeded continuing with installation.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Errors during DKMS module removal
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0

Creating symlink /var/lib/dkms/fglrx/8.961/source ->
                 /usr/src/fglrx-8.961

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.961/build; sh make.sh --nohints --uname_r=3.2.0-24-gene
ric --norootcheck.....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.961 with DKMS
[Error] Kernel Module : Removing fglrx-8.961 from DKMS

------------------------------
Deleting module version: 8.961
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs
pep@pepubuntu:~/catalyst12.4$ ^C
pep@pepubuntu:~/catalyst12.4$

---

### Post by Daerun on 2012-05-11
Aquest error que poses, quan et surt? Vull dir, en quin punt concret del tutorial que enllaces t'apareixen aquests missatges?

---

### Post by akyra on 2012-05-11
Hola,

Prova a utilitzar els drivers lliures no els privatius, en la versió anterior donaven problemes.

Per fer això ves a Sistema->Controladors Restringits i deshabilitals, a veure que tal et va.

Adeu.

---

### Post by wgarcia on 2012-05-12
A les Notes de Llançament de la versió 12.04 posa que pot haver-hi un error reportat i en vies de solució amb aquest model de targeta:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes)

tot i que el que diu és que l'usuari s'enfronta amb una pantalla negra en iniciar l'ordinador, que em sembla que no és el teu cas. Si mires l'informe d'error (cliques el número que surt a la línia on es menciona aquesta targeta) em sembla que també suggereixen dreceres mentre no s'arregli.

---

