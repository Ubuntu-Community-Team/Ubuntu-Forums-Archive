---
title: "[SOLVED] Problema de permisos"
date: 2007-09-12
forum: Catalan Team
---

### Post by Cocoguagua on 2007-09-12
Salutacions

Ahir vaig instalar l'ubuntu 7.04 a un ordinador amb dos discs durs. El primer de 80 gigas per al sistema i l'altre, de 200 gigas, per als documents de l'usuari. Durant la instalació no vaig tenir cap problema, però un cop reiniciat cada cop que vull accedir el disc dels documents em demana la contrassenya de root.

En un primer moment vaig pensar que eren els permisos i els vaig canviar de root a usuari (almenys al disc dels documents),  però cada cop que entro al sistema em segueix demanant la contrassenya. A més, em surt un missate que diu (més o menys): "aquest usuari no té permisos per utillitar discs interns). Algú sap com ho puc arreglar? Gràcies.

---

### Post by papapep on 2007-09-12
Enganxa'ns el contingut del fitxer** /etc/fstab**

---

### Post by Cocoguagua on 2007-09-12
Aquí ho tens:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0acae606-f448-449e-a15b-cb67748ae398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c3cefbd4-ebd5-4453-b59e-06a6fd1270dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by ilku on 2007-09-13
En aquest "/fstab" no veig pas la partició d'un segon disc dur, simplement veig que tens 2 cd/dvd :).
El mes segur es que et demani la contrasenya de root per montar aquest disc, ja que de entrada no esta muntat.

---

### Post by papapep on 2007-09-13
Tal i com et diu l'ilku, el sistema no et munta el segon disc al arrencar, amb el qual, com que muntar i desmuntar es tasca d'administració, quan tu el vols fer servir et demana la contrassenya. Pura lògica de seguretat :-D

Quan vas instal·lar l'Ubuntu vas particionar manualment els discs, o vas dir-li que ho fes ell solet tot??

---

### Post by Cocoguagua on 2007-09-13
Ho vaig fer manuamlent amb un CD Live del Gparted i vaig donar format Ext3 el segon disc, que ara no em reconiex. Després per instalar l'ubuntu vaig utilitzar el primer disc sencer.

---

### Post by papapep on 2007-09-13
> Després per instalar l'ubuntu vaig utilitzar el primer disc sencer.

Aleshores com vols que Ubuntu sàpiga que vols muntar el segon disc com a /home??? :-D No té super-poders adivinatius, com diria apt-get moo...

Ara et cal afegir el punt de montatge /home i la unitat /dev/sdaX (amb el número que tingui el segon disc dur) al /etc/fstab per a que t'ho faci al arrencar i, posteriorment, copiar totes les dades del teu antic /home al nou.

---

### Post by Cocoguagua on 2007-09-13
Ok. Doncs ara ho provaré d'arreglar i gràcies.

---

### Post by Cocoguagua on 2007-09-13
Salutacions de nou.

He afegit el disc a fstab però em segueix demanat la contrassenya.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0acae606-f448-449e-a15b-cb67748ae398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c3cefbd4-ebd5-4453-b59e-06a6fd1270dc none            swap    sw              0       0
/dev/sdb
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

On hi ha el problema ara?

---

### Post by orestesmas on 2007-09-13
> **Cocoguagua said:**
> Salutacions de nou.

He afegit el disc a fstab però em segueix demanat la contrassenya.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb

On hi ha el problema ara?

Aquest "sdb" solet no és res. El sistema l'ignora. Fa referència a TOT el disc, i no pas a una partició concreta del disc. A més, compara-ho amb la resta de línies: la teva està incompleta.

Fes una cosa: obre un terminal i fes un "copia i enganxa" de la sortida de la següent ordre:

ls -l /dev/disk/by-uuid/

Amb això podrem saber la UUID assignada a la partició del teu disc i amb aquesta informació podràs posar la línia correcta al fstab.

---

### Post by Cocoguagua on 2007-09-13
0acae606-f448-449e-a15b-cb67748ae398 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-09-13 14:40 9cc299ae-ef67-413c-a20f-c3a2a6485c27 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-09-13 14:40 c3cefbd4-ebd5-4453-b59e-06a6fd1270dc -> ../../sda5

---

### Post by papapep on 2007-09-13
Doncs, si no vaig errat, has de ficar al /etc/fstab, el següent:

```
UUID=9cc299ae-ef67-413c-a20f-c3a2a6485c27 /home ext3 defaults,errors=remount-ro 0 1
```

I no oblidis eliminar el que has afegit abans.

---

### Post by Cocoguagua on 2007-09-13
Papapep he afegit el que m'has donat però no podia entrar al sistema per un error en la carpeta de home. Finalment he aconseguit entrar en mode text i he eliminat la referència home.

Tal volta m'he explicat malament i el que jo vull es que el segon disc dur sigui el de  les meves dades, peró ja el va bé que la carpeta de home estigui a primer disc. El problema és no poder accedir el segon disc sense haver de escriure la contrassenya.


Bé, ara el fstab és el següent, però ara ja no puc ni 'veure' el disc. No em surt per enlloc.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0acae606-f448-449e-a15b-cb67748ae398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c3cefbd4-ebd5-4453-b59e-06a6fd1270dc none            swap    sw              0       0
UUID=9cc299ae-ef67-413c-a20f-c3a2a6485c27 /  ext3 defaults,errors=remount-ro 0 1

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by RainCT on 2007-09-13
Prova fent un directori anomenat "dades" al home i amb la línia:

```
UUID=9cc299ae-ef67-413c-a20f-c3a2a6485c27 /home/dades ext3 defaults,errors=remount-ro 0 1
```

---

### Post by Cocoguagua on 2007-09-13
Igual que abans. Ara ni tan sols puc veure el disc en qüestió.

---

### Post by papapep on 2007-09-13
A veure, mostra'ns el fstab que tens ara.

---

### Post by Cocoguagua on 2007-09-13
Així em reconeix el disc però em demana la contrassenya per accedir als documents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0acae606-f448-449e-a15b-cb67748ae398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c3cefbd4-ebd5-4453-b59e-06a6fd1270dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0



En canvi així, el disc no està visible:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0acae606-f448-449e-a15b-cb67748ae398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c3cefbd4-ebd5-4453-b59e-06a6fd1270dc none            swap    sw              0       0
UUID=9cc299ae-ef67-413c-a20f-c3a2a6485c27 /home/dades ext3 defaults,errors=remount-ro 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

Per cert, no sé si està relacionat, però ara tampoc em reconeix els USB portàtils.

---

### Post by papapep on 2007-09-13
Tens un directori que es diu "dades" dins el /home?? Si és així, aquí tens el disc dur. 

Si no és així, crea el directori: 

```
sudo mkdir /home/dades
```

i munta'l:

```
sudo mount /dev/sdb1 /home/dades
```

Ara ja l'hauries de tenir disponible.

---

### Post by Cocoguagua on 2007-09-13
:). Perfecte. Ja el tenc disponible i operatiu al 100%. Gràcies a tots per la vostra ajuda!!!

---

