---
title: "[SOLVED] Acces al disc dur de Windows des de Kubuntu"
date: 2007-07-05
forum: Catalan Team
---

### Post by noidartes on 2007-07-05
Hola Familia,

Sóc molt nou amb això de linux. Primer de tot dir que el que acabo d'instalar és la distro Kubuntu encara que postejo aqui ja que és la web que m'han recomanat i crec que funcionen molt similar. 

El tema és que utilitzo molt el pc per mirar pelicules i escoltar musica i ho tinc tot al disc dur de windows (tinc xp i kubuntu al portàtil). La meva pregunta  és: Hi ha alguna manera fàcil d'accedir al disc dur de manera que no estigui grabant cd's per passar l'informació d'un sistema o altre? Alguna aplicació que em pugui ajudar a fer això? De fet el que m'interessa és només llegir, no tinc necessitat de grabar-hi en principi. :p

Gràcies i salut!
Albert

---

### Post by jmaspons on 2007-07-05
Benvingut!
Primerament que sàpigues que això és territori de kubuntuaires, ubuntaires i altres subespècies encara que els millors som els kubuntaires :)

Si durant la intal·lació vas dir on volies que et muntés la partició de windows ja hauries de trobar la carpeta. Si no pots provar de configurar-ho des d'"Arranjament del sistema" >> Disk &  Filesystems" (a la pestanya "avançat"). Aquí veuràs les particions que hi ha i podràs configurar si es munten automaticament, on  i altres coses.

El més habitual és muntar-ho a /media/xxxxx així quan vagis a suports d'emmagatzematge ja veuràs les particions.

Salut!

---

### Post by noidartes on 2007-07-05
Per instalar vaig fer més petita la partició de windows i a la instalació de kubuntu simplement li vaig dir que utilitzes l'espai del disc lliure. O sigui que tot això de muntar particions no ho vaig haver de fer manualment. 

Aquest vespre donaré un altre cop d'ull a veure si trobo la carpeta però no em sona d'haber-la vist. 

Seguiré informant ;)

---

### Post by noidartes on 2007-07-05
Ja he provat de fer això i no podia pas anar pitjor. :(

He accedit a "Arranjament del sistema" >> Disk & Filesystems" i he provat de fer canvis. Sense voler crec que s'ha canviat alguna cosa de la partició on i ha el kubuntu. Tot-hi que crec que ho he tornat a deixar igual.

Resultat: a part de no aconseguir accedir a windows des de linux, després de reiniciar el kubuntu no arrenca. després de sortir el logo i abans de demanar la contrasenya es queda penjat en una pantalla totalment negre.

:(

Algú em pot ajudar a solucionar aquest marder? Si és que té solució, clar...  ;)

---

### Post by jmaspons on 2007-07-05
Mira si pots obrir una terminal amb ctrl+alt+F1. Després penja què et surt si escrius "mount" (previament has d'entrar l'usuari i contrasenya). També pots mirar de penjar el contingut de l'arxiu /etc/fstab (obre'l escrivint "nano /etc/fstab").

Si no pots accedir a la línia de comandes hauràs d'utilitzar el live-cd per veure i arreglar si fa falta l'arxiu fstab de l'ubuntu que tens instal·lat.

Si l'has instal·lat fa poc i no hi havies perdut gaire hores afegint programes o configurant coses potser et surtiria més a compte reinstal·lar . Tot i això jo recomano intentar arreglar-ho ja que no crec que sigui un problema gaire complicat i pots aprendre a solucionar-ho o saber on remenar si et trobes amb problemes semblants.

Salut!

---

### Post by noidartes on 2007-07-06
[CENTER][LEFT]Ahir ho vaig provar i si que puc accedir a la línia de comandes, el problema és que després de posar el nom d'usuari i contrassenya em quedo igual, no sé que posar. Vaig provar a escriure aixo que em vas posar mount i em fa com un resum de les particions ?? i si poso /etc/fstab  o nano/etc/fstab  diu que no existeix.

Potser el més senzill serà que provi d'arreglar-ho des del live cd o a reinstalar perque sincerament no se gens com funciona això de la linea de comandes.   :(

---

### Post by jmaspons on 2007-07-06
Prova amb el live-cd si t'hi sents més còmode. Penja el que et surt quan escrius mount i el contingut de fstab (nano /etc/fstab , amb espai, o pots obrir-lo amb el kate).

vinga que te'n sortiràs :)

---

### Post by noidartes on 2007-07-06
Hola. això és el que surt quan poso mount:

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
ubuntu@ubuntu:~$


i això és el que surt quan poso el nano:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

Si ho faig visualment, que m'hi sento més comode la imatge és aquesta. prova de posar el de 15GB que és on hi ha el linux en Enable però no em deixa, em dona error  :(

[IMG]http://www.flogup.net/fotos/07/07/06/140829.jpg[/IMG]

---

### Post by noidartes on 2007-07-10
Editat:

Al final he formatejat la partició i he instal.lat el Kubuntu de nou. El problema és que no m'atrabeixo a tornar a remanar una mica més per veure si aconsegueixo accedir al disc dur de windows. 

Si algu coneix algun manual o alguna manera senzilla de fer-ho sense perill de tornar-ho a trinxar tot...

Moltes Gràcies!!!

---

### Post by orestesmas on 2007-07-11
De fet, el que tu vols fer és força senzill. Linux està pensat justament per connectar-se a un munt de sistemes diferents.

La teoria és simple: només cal que editis el fitxer /etc/fstab (com a superusuari) i afegeixis una línia al final on se li ha d'indicar:
1- La partició on tens el windows
2- El punt de muntatge (el directori (buit) de linux sota el qual vols fer "aparèixer" el disc de windows). Pots crear-lo tu mateix amb "sudo mkdir /mnt/windows", per exemple.
3- El tipus de sistema de fitxers (normalment vfat o ntfs, si és un windows)
4- Algunes opcions

Tens tota aquesta informació a mà? Anem a suposar (tu canvia-ho d'acord amb el teu sistema) que les dades són:
1- /dev/sda1
2- /mnt/windows
3- ntfs

Aleshores la línia que hauries de posar a /etc/fstab és la següent (tot en una sola línia, sense ENTER)

/dev/sda1   /mnt/windows   ntfs   ro,user,umask=0000  0   2

Deses el fitxer modificat i aleshores t'apareixerà una icona de disc als "suports d'emmagatzematge" que podràs clicar i accedir al windows.

També pots afegir un "auto" a les opcions (ro,user,auto,umask=0000) i aleshores el muntarà en arrencar i estarà disponible durant tota l'estona.

M'he explicat prou?

Orestes.

---

### Post by ilku on 2007-07-12
Jo el vaig instal·lar amb la partició feta i me'l muntava automàticament amb una linea semblant a aquesta
```
/dev/sda1 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1 
```
on /dev/sda1 es la partició
/media/hda1 es el punt de muntatge
i la resta ja ho han explicat.

De totes maneres no he provat a escriure res, no se si es podra.

---

### Post by orestesmas on 2007-07-12
Modernament ja es pot escriure a particions NTFS amb el driver ntfs-3g, però jo no ho he provat. Diuen que és segur.

Els paquets a instal·lar són el ntfs-3g i ntfs-config

A la feisty aquests paquets són al repositori *universe*, de manera que estan disponibles de manera immediata.

En [aquesta adreça]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") tens tota la info de com fer-ho.

Sort.

---

### Post by noidartes on 2007-07-12
Moltes gràcies Orestes, sembla fàcil. Ho volia provar ahir però no tenia conexio a internet i no vaig poder entrar al forum. Avui ho provo a veure si me'n surto.

Només un dubte, com entro com a superusuari? Si entro a la consola des de les opcions d'"inici" ja està ok? o he de fer alguna cosa especial?

Salut i moltes gràcies!

---

### Post by orestesmas on 2007-07-12
En la instal·lació per omissió de ubuntu/kubuntu, el superusuari està desactivat, vull dir que no té contrasenya assignada i per tant no pots entrar com a root.

El que si pots fer és "agafar" temporalment els poders de superusuari afegint "sudo " davant de qualsevol ordre de consola (per exemple "sudo rm -f /" t'esborra tot el sistema des de l'arrel, o sia que compte amb el que fas!!).

En usar el "sudo" et demanarà el teu password (no pas el de root), i és capaç de "recordar-lo" durant una estona, per si fas servir més sudos.

També pots assignar un password al root per tal de poder entrar com a ell:
```
sudo passwd root
```

O també et pots fer root sense assignar-li un password gràcies a l'ordre "su" (SuperUser) executada amb sudo:
```
sudo su
```

Està entès?

---

### Post by CarlesOriol on 2007-07-12
Orestes.

Al canal anglès d'irc #ubuntu ensenyar a un novell a escriure sudo passwd és causa de que et maleeixin els ossos fins al sisè any del sisè més del sisè dia de la sisena generació.

---

### Post by noidartes on 2007-07-12
Hola de nou,

he probat de fer això i al intentar editar /etc/fstab em trobo amb el problema que no em deixa entrar perque em diu que tinc l'access denegat. He posat sudo su i introduit el password i tampoc. 

Algu té alguna idea de com accedir-hi?

Merci i salut!

---

### Post by papapep on 2007-07-12
En un terminal fes:

sudo nano /etc/fstab

et demanarà la teva contrassenya i podràs editar l'fstab

per cert, la comanda es composa de tres parts:

sudo --> petició d'executar una comanda amb els drets del super-usuari sense ser-ho

nano ---> simple i efectiu editor de fitxers de text en consola

/etc/fstab --> com ja sabràs, el camí sencer fins al fitxer fstab desde el directori arrel.

---

### Post by noidartes on 2007-07-12
estic pensant ja en tirar la tovallola :(

No me'n surto pas. despres d'editar a /etc/fstab amb la linea que m'heu comentat segueixo sense tenir accés a la partició de windows. He anat a disk settings per mirar-ho gràficament i sembla que els canvis s'han produit però la partició segueix disabled, a la que clico a enable em dona un missatge d'error: An error occurred while enabling /mnt/windows.
The system reported: mount: mount point /mnt/windows does not exist

Gràcies i salut!

---

### Post by papapep on 2007-07-13
Bé, ja has fet una passa més endavant :-)

I aquest directori /mnt/windows, ja existeix realment?? El mount t'està dient que NO existeix. l'has creat??

Sinó ho has fet, tecleja a un terminal:

sudo mkdir /mnt/windows

I torna a provar el que has provat abans. No defalleixis, l'únic que et passa és que no tens experiència.

Salutacions.

---

### Post by noidartes on 2007-07-13
No, no. Mentre em seguiu ajudant jo no defalleixo. El que em sap greu és estar preguntant coses tan elementals :(

Aquest vespre ho provo. Moltes gràcies!

---

### Post by orestesmas on 2007-07-13
Deu ser per això que no em miro mai el canal anglès del irc...

Si assignem contrasenya al root funciona com una debian, o sia que no es fa pas res dolent. Però què t'haig d'explicar a tu!

---

### Post by orestesmas on 2007-07-13
> The system reported: mount: mount point /mnt/windows does not exist

El missatge ja t'ho diu clarament: has de crear primer el directori on muntaràs la partició de windows. Sembla lògic, no?

Ah, ara veig que el papapep també t'ho deia en un missatge.

---

### Post by noidartes on 2007-07-13
Ho acabo d'aconseguir :)

Només us volia donar les gràcies a tots els que ho heu fet possible. 

Moltes gràcies de veritat!

---

