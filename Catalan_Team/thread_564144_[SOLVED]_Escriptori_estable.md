---
title: "[SOLVED] Escriptori estable"
date: 2007-09-30
forum: Catalan Team
---

### Post by siscuboontu on 2007-09-30
[FONT="Arial"][SIZE="2"][/SIZE][/FONT]

Hola un altre cop!

Resulta que sóc professor d'institut i de tant en tant faig anar una aula d'informàtica amb ordinadors duals. M'interessa molt fer anar l'ubuntu però hores d'ara tinc dos problemes importants:

1.- No trobo drivers per la impressora que tenim connectada en xarxa (Ricoh Aficio 1060), per la qual cosa no podem imprimir des dels ordinadors amb ubuntu (12 en aquesta aula i 3 a la sala de profes), la qual cosa representa una pega a l'hora de difondre l'ubuntu.

2.- No sé com fer que l'escriptori es mantingui estable després d'haver-hi treballat. És a dir, hi ha alguna cosa semblant al congelador de Pharonics per Windows? Amb això s'evitaria haver de configurar l'escriptori cada cop que alguna persona hi deixa algun document o desmunta alguna unitat de xarxa.

Moltíssimes gràcies per avançat!
:guitar:

---

### Post by papapep on 2007-10-01
Respecte l'impressora, aquí:

[http://openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_1060](http://openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_1060)

diu que t'hauria de funcionar perfectament amb un controlador genèric PCL-5e.

---

### Post by albertg on 2007-10-01
Una opció força senzilla per al segon problema (però utilitzat la línia d'ordres), és esborrar i crear de nou el directori d'inici de l'usuari a partir d'una plantilla, cada cop que s'inicïi l'Ubuntu (no sé si és exactament el que vols). Els passos serien els següents:

1. Configura l'escriptori de l'usuari tal com vulguis.

2. Executa en un terminal:
```
sudo rsync -a --del /home/usuari/ /home/usuari-estable/
```

Això fa una còpia del contingut del directori personal de l'usuari.

3. Edita el fitxer /etc/rc.local i escriu el següent:
```
#!/bin/sh -e
rsync -a --del /home/usuari-estable/ /home/usuari/
exit 0
```

D'aquesta manera es restablirà el directori de l'usuari a partir de la còpia realitzada anteriorment, cada cop que s'iniciï l'Ubuntu.

Si vols fer canvis permanents a l'escriptori has de tornar a fer una còpia del directori de l'usuari amb el pas 2.

---

### Post by siscuboontu on 2007-10-01
Moltes gràcies albertg, sí que és aquesta la idea, demà ho provaré i ja us diré.

---

### Post by siscuboontu on 2007-10-02
Em sap greu però avui no he pogut provar les solucions que m'havíeu proposat. Potser demà, ja us diré.

Gràcies.

---

### Post by siscuboontu on 2007-10-03
Alberg, acabo de provar la solució que has proposat i me n'he sortit. Moltes gràcies.

Ara només falta tenir temps per provar amb la impressora.):P

---

### Post by sianeu on 2007-10-03
Es molt interessant aixó, però em ve una pregunta: borra tambè els arxius ocults (els que es crean al instal·lar un programa)?

Salut

---

### Post by papapep on 2007-10-03
Prova-ho tu mateix. Símplement crea un fitxer que comenci amb un punt (.nomfitxer) i verifica si l'esborra o no. ;-)

---

### Post by sianeu on 2007-10-03
Vale !. Però ara que m'en adono, primer hauria de saber cóm es tira erera l'invent. No vull haver de fer copies cada vegada que vulgui entrar alguna cosa al directori personal !!!  :)

Salut

---

### Post by siscuboontu on 2007-10-03
Hola papapep,

He provat d'instal·lar els drivers de la pàgina [http://openprinting.org/show_printer...oh-Aficio_1060](http://openprinting.org/show_printer...oh-Aficio_1060) com havies proposat (he provat les dues opcions) i no me'n surto. Ubuntu la reconeix i la identifica (amb IP i port) però quan envio una pàgina de prova no li arriba. Quin pot ser el problema? Que l'usuari no estigui reconegut? Val a dir que la impressora en Windows fa servir SmartNetMonitor com a gestor de ports i usuaris (crec), i no sé si això pot tenir alguna cosa a veure.

Gràcies.

---

### Post by papapep on 2007-10-03
**siscuboontu**:

> He provat d'instal·lar els drivers de la pàgina...

Que jo sàpiga no et feia falta instal·lar res. Els drivers genèrics PCL (entre ells el PCL5e) crec que venen "de sèrie" amb el cups i ubuntu.

> Quin pot ser el problema? Que l'usuari no estigui reconegut?

Usuari?? Gestiona usuaris la teva impressora?? Aleshores tot es complica bastant, clar...aquí ja no et puc ajudar.

Respecte la configuració del driver (usuaris a banda) si expliques quins paràmetres has emprat en concret, potser podrem tenir més pistes.

> Val a dir que la impressora en Windows fa servir SmartNetMonitor com a gestor de ports i usuaris

No tinc ni la més remota idea de què estàs parlant...

**sianeu**:

> Però ara que m'en adono, primer hauria de saber cóm es tira erera l'invent. No vull haver de fer copies cada vegada que vulgui entrar alguna cosa al directori personal !!!

Crec que no acabo d'entendre què vols dir.

---

### Post by albertg on 2007-10-03
> **sianeu said:**
> Es molt interessant aixó, però em ve una pregunta: borra tambè els arxius ocults (els que es crean al instal·lar un programa)?

Sí, s'esborren tots.

---

### Post by albertg on 2007-10-03
> **sianeu said:**
> Vale !. Però ara que m'en adono, primer hauria de saber cóm es tira erera l'invent. No vull haver de fer copies cada vegada que vulgui entrar alguna cosa al directori personal !!!  :)


Només cal desfer els canvis fets al fitxer /etc/rc.local, esborrant la linia:
```

rsync -a --del /home/usuari-estable/ /home/usuari/

```

---

### Post by sianeu on 2007-10-03
Gracies albertg, ja em queda clar. Només una última qüestio: que passa amb el programa afectat per la "neteja"?  Tornará a crear el directori ocult o quedará "trencat" com a brossa pel sistema?

Salut

---

### Post by albertg on 2007-10-03
> **sianeu said:**
> Gracies albertg, ja em queda clar. Només una última qüestio: que passa amb el programa afectat per la "neteja"?  Tornará a crear el directori ocult o quedará "trencat" com a brossa pel sistema?

No entenc a què et referieixes, la  còpia i la restauració es fan de tot el contingut del directori personal (directoris ocults inclosos).

---

### Post by siscuboontu on 2007-10-03
papapep, disculpa la meua ignorància, de fet sóc un novell en temes informàtics, però estic força decidit a fer servir linux i programari lliure exclusivament (encara he de convèncer a la meua parella i a uns quants companys de feina, però "estamos en ello".

De fet tens raó que no m'has parlat en cap moment d'instal·lar res, en qualsevol cas sí que he canviat els .ppd del web [http://openprinting.org/show_printer...oh-Aficio_1060](http://openprinting.org/show_printer...oh-Aficio_1060) i llavors passa el que he comentat. També he de disculpar-me pel tema dels usuaris, no estic del tot segur de si realment és així, diria que sí però me'n assabentaré del cert abans de continuar per aquesta línia. El que és segur és que en el "finestres" la gestió d'usuaris i altres paràmetres està relacionada amb el programa SmartNetMonitor.

De tota forma, miraré detalls de la configuració del driver per tal de donar el màxim de pistes possibles.

Moltes gràcies,

Sisco.

---

### Post by sianeu on 2007-10-05
> No entenc a què et referieixes, la còpia i la restauració es fan de tot el contingut del directori personal (directoris ocults inclosos).

Vull dir que si, entre altres coses, s'ha instal·lat un programa que ha deixat un directori ocult (preferencies... el que sigui) a la carpeta del usuari, aleshores que pasa amb aquest programa quan es restaura la carpeta del usuari a la posiciò anterior (i, per tant, aquest directori queda borrat). El programa queda fet malbè però no desinstal·lat, o el  programa torna a crear el directori ocult . No se si ara m'explicat millor.

Salut

---

### Post by albertg on 2007-10-06
> **sianeu said:**
> Vull dir que si, entre altres coses, s'ha instal·lat un programa que ha deixat un directori ocult (preferencies... el que sigui) a la carpeta del usuari, aleshores que pasa amb aquest programa quan es restaura la carpeta del usuari a la posiciò anterior (i, per tant, aquest directori queda borrat). El programa queda fet malbè però no desinstal·lat, o el  programa torna a crear el directori ocult . No se si ara m'explicat millor.

Salut

Els programes només deixen fitxers de configuració al directori personal, i si s'esborra un d'aquests directoris, el programa els torna crear com si l'executessis per primera vegada. En aquest sentit no hi ha problema, només has d'anar en compte en perdre dades que vols conservar (per oblidar-te d'actualitzar la còpia).

---

### Post by SiscoGarcia on 2008-05-30
Hola bon dia,

Reobro aquest fil perquè després d'haver-lo fet servir amb èxit durant un curs sencer, em trobo que la solució que va donar al seu dia albertg i que tan bé m'ha anat:

> **albertg said:**
> Una opció força senzilla per al segon problema (però utilitzat la línia d'ordres), és esborrar i crear de nou el directori d'inici de l'usuari a partir d'una plantilla, cada cop que s'inicïi l'Ubuntu (no sé si és exactament el que vols). Els passos serien els següents:

1. Configura l'escriptori de l'usuari tal com vulguis.

2. Executa en un terminal:
```
sudo rsync -a --del /home/usuari/ /home/usuari-estable/
```

Això fa una còpia del contingut del directori personal de l'usuari.

3. Edita el fitxer /etc/rc.local i escriu el següent:
```
#!/bin/sh -e
rsync -a --del /home/usuari-estable/ /home/usuari/
exit 0
```

D'aquesta manera es restablirà el directori de l'usuari a partir de la còpia realitzada anteriorment, cada cop que s'iniciï l'Ubuntu.

Si vols fer canvis permanents a l'escriptori has de tornar a fer una còpia del directori de l'usuari amb el pas 2.



 amb l'actualització a la Hardy deixa de funcionar, aparentment pel canvi de gnome-vfs a gvfs. Textualment diu:

```
rsync: readlink "/home/alum-01/.gvfs" failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files could not be transferred (code 23) at main.c (977) [sender=2.6.9]
```

Alguna idea?

Gràcies.

---

### Post by papapep on 2008-05-30
> Alguna idea?


Sí :-D

que sense veure la ordre exacta que executes, ni els permisos dels directoris que estas intentant sincronitzar (ls -la) no tenim base per pensar...

---

### Post by SiscoGarcia on 2008-05-31
Sort que tens bones idees, Josep, com sempre ;)

Tens raó, jo em pensava que amb la informació que passava ja n'hi havia prou, però ja veig que és insuficient.

Dilluns quan estigui al davant de la màquina segueixo informant.

Gràcies.

---

### Post by SiscoGarcia on 2008-06-02
El problema amb aquest fil em sembla que serà la falta de continuïtat, però poc a poc a veure si ho aconseguim. Anem a pams, copio el missatge que em retorna la consola en introduir la primera ordre:

```
usuari@E1-AULA1:~$ sudo rsync -a --del /home/alum-01/ /home/alum-01-estable/
[sudo] password for usuari: 
rsync: readlink "/home/alum-01/.gvfs" failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
usuari@E1-AULA1:~$ 
```

Què més?

---

### Post by papapep on 2008-06-02
He trobat alguna referència sobre que aquest error pot ser degut a que algun fitxer tingui un nom massa llarg (quan s'està tractant unitats amb NTFS, és el cas?) o que tenen caràcters "no normals" al nom: paréntesi, espais, claudators, etc.

Tot i això, un "ls -la" dels directoris sincronitzats, i saber amb quin format de fitxers estem treballant ajudaria.

AFEGITÓ: També aniria bé saber que tens a /etc/fstab i /etc/mtab.

---

### Post by SiscoGarcia on 2008-06-02
Allà va el "ls -la" del directori problemàtic (el de l'usuari alum-01):

```
 ls -la
ls: no s’ha pogut accedir a .gvfs: Permission denied
total 144
drwxr-xr-x 26 alum-01 alum-01 4096 2008-06-02 13:17 .
drwxr-xr-x  5 root    root    4096 2008-05-30 12:16 ..
-rw-------  1 alum-01 alum-01   28 2008-05-30 12:18 .bash_history
-rw-r--r--  1 alum-01 alum-01  220 2008-05-30 12:14 .bash_logout
-rw-r--r--  1 alum-01 alum-01 2940 2008-05-30 12:14 .bashrc
drwxr-xr-x  3 alum-01 alum-01 4096 2008-05-30 12:14 .cache
drwxr-xr-x  4 alum-01 alum-01 4096 2008-05-30 12:15 .config
-rw-------  1 alum-01 alum-01   28 2008-06-02 12:24 .dmrc
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 Documents
drwxr-xr-x  2 alum-01 alum-01 4096 2008-06-02 13:16 Escriptori
-rw-------  1 alum-01 alum-01   16 2008-05-30 12:14 .esd_auth
lrwxrwxrwx  1 alum-01 alum-01   26 2008-05-30 12:14 Examples -> /usr/share/example-content
drwx------  4 alum-01 alum-01 4096 2008-06-02 12:24 .gconf
drwx------  2 alum-01 alum-01 4096 2008-06-02 13:16 .gconfd
drwx------  7 alum-01 alum-01 4096 2008-05-30 12:14 .gnome2
drwx------  2 alum-01 alum-01 4096 2008-05-30 12:14 .gnome2_private
drwx------  2 alum-01 alum-01 4096 2008-06-02 12:24 .gnupg
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 .gstreamer-0.10
-rw-r--r--  1 alum-01 alum-01  126 2008-06-02 13:16 .gtk-bookmarks
d?????????  ? ?       ?          ?                ? .gvfs
-rw-------  1 alum-01 alum-01  326 2008-06-02 12:24 .ICEauthority
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 Imatges
drwxr-xr-x  3 alum-01 alum-01 4096 2008-05-30 12:14 .local
drwx------  3 alum-01 alum-01 4096 2008-05-30 12:14 .metacity
drwx------  3 alum-01 alum-01 4096 2008-05-30 12:17 .mozilla
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 Música
drwxr-xr-x  3 alum-01 alum-01 4096 2008-05-30 12:14 .nautilus
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 Plantilles
-rw-r--r--  1 alum-01 alum-01  586 2008-05-30 12:14 .profile
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 Públic
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 .pulse
-rw-------  1 alum-01 alum-01  256 2008-05-30 12:14 .pulse-cookie
drwx------  2 alum-01 alum-01 4096 2008-05-30 12:14 .ssh
-rw-r--r--  1 alum-01 alum-01    0 2008-05-30 12:16 .sudo_as_admin_successful
drwx------  3 alum-01 alum-01 4096 2008-06-02 13:17 .thumbnails
drwx------  2 alum-01 alum-01 4096 2008-05-30 12:14 .update-notifier
drwxr-xr-x  2 alum-01 alum-01 4096 2008-05-30 12:14 Vídeos
-rw-------  1 alum-01 alum-01  240 2008-06-02 12:24 .Xauthority
-rw-r--r--  1 alum-01 alum-01 2587 2008-06-02 13:16 .xsession-errors
usuari@E1-AULA1:/home/alum-01$ 
```


aquí va el fstab:

```
usuari@E1-AULA1:/etc$ cat fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=42da6ee5-eed1-4f1d-8e1f-347575914fd5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0ffa2316-7c65-4a06-9d65-56c0f4e73dc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


aquí va el mtab:

```
usuari@E1-AULA1:/etc$ cat mtab 
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/usuari/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=usuari 0 0
gvfs-fuse-daemon /home/alum-01/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=alum-01 0 0
```

Esperem notícies ;)

---

### Post by papapep on 2008-06-02
Doncs mirant-ho més a fons, crec que no deus tenir un problema "real". Crec que el tema és que com que de Gutsy a Hardy un dels canvis importants és la incorporacio de gvfs com a gestor del sistema de fitxers gràfic, l'rsync es queixa de que no pot accedir a .gvfs, el qual és correcte, i per això t'ho diu.
Jo provaria a verificar si realment sincronitza els dos directoris correctament i, posteriorment, li diria a l'rsync que exclogui .gvfs dels directoris a sincronitzar.
Si no recordo malament era afegint l'opció (consulta el man per assegurar la jugada):

```
--exclude '/home/alum-01/.gvfs'
```

a la ordre del rsync.

---

### Post by SiscoGarcia on 2008-06-02
Demà ho provaré i ja et diré.

---

### Post by SiscoGarcia on 2008-06-03
\\:D/=D>

Provat i aconseguit! Moltes gràcies, tornaré a marcar el fil com a resolt.

---

