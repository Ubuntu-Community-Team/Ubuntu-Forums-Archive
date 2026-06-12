---
title: "actualització al 12.04 LT"
date: 2012-09-28
forum: Catalan Team
---

### Post by jinglada on 2012-09-28
Hola companys,

Acabo de fer l'actualització al 12.04 LT i estic atabalat. No em surt la barra del menú on hi havia Aplicacions, i dues coses més que ara no recordo, des d'on podia accedir a Administració i Sistema. 

Com es fa per instalar aquesta barra superior o com s'accedeix a Administració i Sistema?

El ventilador no para mai. Que he de fer per a què s'engegui només quan calgui?

Per al seguiment de les temperatures que em recomaneu, el Psensor o el Xsensors?

De moment no he trobat cap més problema.

Gràcies a la bestreta.

---

### Post by ffp on 2012-09-28
Vaja,
T'has trobat de cop amb l'Unity, nou entorn d'escriptori des del 10.10 crec.
A mi em va liar molt al principi, però ara ja m'he acostumat, i tinc mes embolics amb el gnome classic.
Tens 2 opcions començar a acostumar-te al Unity o carregar gnome clàssic. El centre de programari el tens a la barra lateral esquerra clicas 1 vegada.
El programes habituals també son allà.
La administració del sistema (reduïda) la trobarás al botó d'apagada, botó de ratolí dret i "Paràmetres del Sistema".
Per el control de temperatura no funciona cap applet de gnome, jo ho he sol·lucionat amb conky.
El control del ventilador (suposo que es un portàtil), no en se res.

Au a investigar! Sort!

---

### Post by jinglada on 2012-09-28
Gràcies ffp! A espavilar-nos, com sempre ;-) I el que s'aprén, que no val per res? ;-)

---

### Post by jinglada on 2012-09-28
> **jinglada said:**
> Gràcies ffp! A espavilar-nos, com sempre ;-) I el que s'aprén, que no val per res? ;-)
Per al control de temperatura he instal·lat el Psensor que ve en el "Centre de programari". 
He trobat també, a la mateixa barra els "Paràmetres del Sistema".

Pel que fa al ventilador he trobat això: [http://www.linuxnoveles.com/2011/controlar-el-uso-del-ventilador-en-ubuntu/](http://www.linuxnoveles.com/2011/controlar-el-uso-del-ventilador-en-ubuntu/) que diu que he de fer el següent:

sudo apt-get install sensors-applet
sudo sensors-detect
gksudo gedit /etc/default/grub, o bé,  sudo nano /etc/default/grub

substituir la línea 
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; 
per 
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash acpi_osi=Linux&#8221;

i reiniciar el sistema

Em podeu dir si això és correcte?

---

### Post by jinglada on 2012-09-28
D'entrada el /etc/default/grub no el troba i fent 
whereis grub
dóna:
grub: /usr/sbin/grub /etc/grub.d /usr/lib/grub /usr/share/grub /usr/share/man/man8/grub.8.gz
llavors quin he d'usar /usr/sbin/grub o /usr/lib/grub o /usr/share/grub?

---

### Post by jinglada on 2012-09-28
Com es fa per a "Reiniciar"?

On es veuen les aplicacions obertes? Ara ho veig; amb uns fletxetes blanques al costat esquerra del botó de l'aplicació.

Un altre tema és que ara em quedo sense espai al disc. Tenia 3Gb lliures abans d'actualitzar.

---

### Post by wgarcia on 2012-09-29
L'opció de reiniciar surt com a botó a la finestra que s'obre quan esculls "Surt". Per a la versió 12.10 ja ho han tornat a posar com a opció separada el menú de l'indicador. 

Quant a l'espai lliure, quant et queda ara? Sembla estrany perquè l'espai ocupat (i lliure) hauria de ser més o menys el mateix després de l'actualització.

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> L'opció de reiniciar surt com a botó a la finestra que s'obre quan esculls "Surt". Per a la versió 12.10 ja ho han tornat a posar com a opció separada el menú de l'indicador. 

Quant a l'espai lliure, quant et queda ara? Sembla estrany perquè l'espai ocupat (i lliure) hauria de ser més o menys el mateix després de l'actualització.

Gràcies per la resposta, wgarcia.

Si premo "Surt" em surt això: "Esteu segur que voleu tancar tots els programes i finalitzar la sessió en aquest ordinador?"

Ara tinc 385,2 MB d'espai lliure, però fa 2 hores em deia 0.

Em pots dir alguna cosa respecte al ventilador que no para de funcionar?

I sobre el /etc/default/grub que no hi és?

Porto des de les 8 buscant per internet i no he fet res del que havia de fer. Ser lliures és bonic però és costós. Cal tenir molta fe i esperança en que gràcies a la meva persistència els meus néts tindran un món millor ;-)

---

### Post by wgarcia on 2012-09-29
Sobre "reiniciar", perdona: volia dir prémer "Atura", i al diàleg t'hauria de sortir "Reinicia".

Quant a l'espai lliure, potser tens molts nuclis antics instal·lat. Normalment convé deixar un o dos antics per si hi ha algun problema en el nucli actual poder iniciar el sistema, amb això hi ha prou. Per veure si tens molts nuclis instal·lats pots obrir una terminal i fer

```
ls /boot
```

i aquí veurem si tens moltes "imatges" instal·lades.

---

### Post by wgarcia on 2012-09-29
Quant al ventilador, sembla un problema de targeta gràfica. Saps quin model de targeta gràfica té el teu ordinador? Si no ho saps pots donar la següent instrucció a una terminal i t'ho dirà:

```
lspci | grep -i vga
```

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> Sobre "reiniciar", perdona: volia dir prémer "Atura", i al diàleg t'hauria de sortir "Reinicia".

Quant a l'espai lliure, potser tens molts nuclis antics instal·lat. Normalment convé deixar un o dos antics per si hi ha algun problema en el nucli actual poder iniciar el sistema, amb això hi ha prou. Per veure si tens molts nuclis instal·lats pots obrir una terminal i fer

```
ls /boot
```

i aquí veurem si tens moltes "imatges" instal·lades.

> No se que deu passar, mira què diu al clicar Atura:

"Esteu segur que voleu tancar tots els programes i aturar l'ordinador?"

Òndia, perdona wgarcia, ara veig el "Reinicia" a l'esquerra de la caixeta del missatge que deia abans. Gràcies.

--------------------------------------
fent 
joan@joan-laptop:/etc/default$ ls /boot > boot.txt

dóna això

abi-2.6.27-14-generic
abi-2.6.28-17-generic
abi-2.6.32-43-generic
abi-3.2.0-31-generic
config-2.6.27-14-generic
config-2.6.28-17-generic
config-2.6.32-43-generic
config-3.2.0-31-generic
grub
initrd.img-2.6.27-14-generic
initrd.img-2.6.28-17-generic
initrd.img-2.6.32-43-generic
initrd.img-3.2.0-31-generic
memtest86+.bin
memtest86+_multiboot.bin
System.map-2.6.27-14-generic
System.map-2.6.28-17-generic
System.map-2.6.32-43-generic
System.map-3.2.0-31-generic
vmcoreinfo-2.6.27-14-generic
vmcoreinfo-2.6.28-17-generic
vmcoreinfo-2.6.32-43-generic
vmlinuz-2.6.27-14-generic
vmlinuz-2.6.28-17-generic
vmlinuz-2.6.32-43-generic
vmlinuz-3.2.0-31-generic

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> Quant al ventilador, sembla un problema de targeta gràfica. Saps quin model de targeta gràfica té el teu ordinador? Si no ho saps pots donar la següent instrucció a una terminal i t'ho dirà:

```
lspci | grep -i vga
```

joan@joan-laptop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV635 [Mobility Radeon HD 3650]
joan@joan-laptop:~$

És la que em van reparar a primers de mes. Amb la versió 10.04 que tenia fins ahir al matí, anava bé.

---

### Post by wgarcia on 2012-09-29
Tens 4 nuclis instal·lats, els 2.6.27, 2.6.28, 2.6.32 i 3.2.0. Deixant aquests dos últims és suficient i t'alliberarà una mica d'espai. El que fa servir la versió 12.04 és el 3.2.0.

Per desintal·lar-los des d'una terminal pots fer:

```
sudo apt-get remove linux-image-2.6.27-14-generic linux-image-2.6.28-17-generic
```

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> Tens 4 nuclis instal·lats, els 2.6.27, 2.6.28, 2.6.32 i 3.2.0. Deixant aquests dos últims és suficient i t'alliberarà una mica d'espai. El que fa servir la versió 12.04 és el 3.2.0.

Per desintal·lar-los des d'una terminal pots fer:

```
sudo apt-get remove linux-image-2.6.27-14-generic linux-image-2.6.28-17-generic
```

Fet! Però l'espai que m'ha alliberat no em serveix de gaire perquè, mea culpa, no vaig dir que tinc una partició per al programari i una altre per al /home i és en el /home que tenia 3 Gb lliures abans d'actualitzar i ara em diu que en queden 300 Mb. Com es pot fer per veure quins fitxers han incrementat ocupació des d'ahir?

---

### Post by wgarcia on 2012-09-29
Això és més estrany, perquè al /home l'actualització no hauria de posar res. 

Si vols investigar una mica l'utilització de l'espai, una comanda molt útil és "du". Té moltes opcions, que pots investigar fent "man du" des d'una terminal. També des d'una terminal si fas 

```
du
```

et mostrarà les carpetes i subcarpetes del directori on el llencis i els seus subdirectoris.

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> Això és més estrany, perquè al /home l'actualització no hauria de posar res. 

Si vols investigar una mica l'utilització de l'espai, una comanda molt útil és "du". Té moltes opcions, que pots investigar fent "man du" des d'una terminal. També des d'una terminal si fas 

```
du
```

et mostrarà les carpetes i subcarpetes del directori on el llencis i els seus subdirectoris.

Ho aniré provant. Gràcies altra vegada.

Pel que fa al ventilador puc provar això que vaig dir en un post al principi?: 

sudo apt-get install sensors-applet
sudo sensors-detect

I com que no tinc el /etc/default/grub

com es podria fer que actués la següent sentència?

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash acpi_osi=Linux”

i reiniciar el sistema

Em pots dir si això és correcte?

---

### Post by wgarcia on 2012-09-30
Doncs si vols afegir una línia a l'arrencada, sí que necessitaries el /etc/default/grub. 

El primer que s'hauria d'intentar és:

```
sudo apt-get install --reinstall grub-common
```

a veure si et restitueix aquest fitxer. 

De totes maneres com et comentava en un altre lloc el problema del ventilador pot ser causat per un controlador inadequat de la targeta gràfica. Depenent quina sigui i quin controlador estigui utilitzant, es pot provar amb controladors propietaris o lliures a veure si ho millora.

---

### Post by ffp on 2012-09-30
> **jinglada said:**
> Per al control de temperatura he instal·lat el Psensor que ve en el "Centre de programari". 
He trobat també, a la mateixa barra els "Paràmetres del Sistema".

Vaja, això no ho havia provat, funciona molt be, moltes gràcies !

> **jinglada said:**
> Pel que fa al ventilador he trobat això: [http://www.linuxnoveles.com/2011/controlar-el-uso-del-ventilador-en-ubuntu/](http://www.linuxnoveles.com/2011/controlar-el-uso-del-ventilador-en-ubuntu/) que diu que he de fer el següent:

Em podeu dir si això és correcte?

Compte que aquestes instruccions no fan esmena al 12.04. I es estrany que no tinguis el /etc/default/grub.
El sensors-applet ni tan sols es als repositoris.
Et funciona el Psensor? si et funciona no cal que instalis res mes ! Pot ser interessant el hddtemp que cerca les temperatures dels discs durs
El sudo sensors-detect es el procediment per registrar els sensors de CPU, ventiladors, etc

---

### Post by jinglada on 2012-09-30
> Originally Posted by wgarcia  
Quant al ventilador, sembla un problema de targeta gràfica. Saps quin model de targeta gràfica té el teu ordinador? Si no ho saps pots donar la següent instrucció a una terminal i t'ho dirà:

Code:
lspci | grep -i vga

> **jinglada said:**
> joan@joan-laptop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV635 [Mobility Radeon HD 3650]
joan@joan-laptop:~$

És la que em van reparar a primers de mes. Amb la versió 10.04 que tenia fins ahir al matí, anava bé.

**Efectivament! He anat a "Paràmetres del sistema" i m'ha sortit la caixeta de missatge "Controladors inicials" que diu:** 
--------------------------------------------
Controlador gràfic de propietat FGLRX d'ATI/AMD (actualitzacions posteriors al llançament)
Comprovat pels desenvolupadors d'Ubuntu
Llicència de propietat
Controlador gràfic de propietat amb acceleració 3D per a targetes ATI.
Cal aquest controlador per a poder utilitzar tot el potencial 3D d'algunes targetes gràfiques d'ATI, així com per donar acceleració 2D a les targetes n
Aquest controlador no està activat.
-----------------------------------------------

**L'he activat i m'ha dit:**

---------------------------------------------
Ha fallat la instal·lació d'aquest controlador.

Consulteu el fitxer de registre per obtenir-ne més detalls: /var/log/jockey.log
----------------------------------------------

**línies "negatives" d'aquest log:**

update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
.....
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
....
2012-09-30 20:27:19,280 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-09-30 20:28:07,733 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-30 20:28:07,747 DEBUG: fglrx_updates is not the alternative in use
2012-09-30 20:28:07,769 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-30 20:28:07,769 DEBUG: fglrx_updates is not the alternative in use

-----------------------------------------------

[B]A sota del missatge primer n'hi ha un alre de semblant que diu:
[/B]
-----------------------------------------------
Controlador gràfic de propietat FGLRX d'ATI/AMD
Comprovat pels desenvolupadors d'Ubuntu
Llicència de propietat
Controlador gràfic de propietat amb acceleració 3D per a targetes ATI.
Cal aquest controlador per a poder utilitzar tot el potencial 3D d'algunes targetes gràfiques d'ATI, així com per donar acceleració 2D a les targetes n
Aquest controlador no està activat.
-------------------------------------------------

**L'he activat i [COLOR="Red"]oh maravella[/COLOR], el ventilador ja es para i s'engega de tant en tant com abans.**

---

### Post by jinglada on 2012-10-01
> **wgarcia said:**
> Això és més estrany, perquè al /home l'actualització no hauria de posar res. 

Si vols investigar una mica l'utilització de l'espai, una comanda molt útil és "du". Té moltes opcions, que pots investigar fent "man du" des d'una terminal. També des d'una terminal si fas 

```
du
```

et mostrarà les carpetes i subcarpetes del directori on el llencis i els seus subdirectoris.

Hi ha alguna manera de detectar els fitxers creats automàticament o involuntàriament en el /home a partir d'una datadeterminada?

He trobat algú que deia que li passava el mateix i que havia trobat el directori 
/home/.Trash-0 molt ple.

Jo l'he buscat i em passa el mateix. El tinc amb 5GB  de fitxers antics, des del 2009 fins el març d'enguany. Amb el Nautilus, perquè no hi tenia accés sense, intento esborrar  el contingut, enviant els fitxers a la paperera i simplement els reanomena.

Com ho puc fer des del terminal? sudo rm .Trash-0 ? (Editat) Em quedaven només 60 kb d'espai lliure. He canviat els permisos i he esborrat els continguts i ara tinc 3,4 Gb lliures segons les propietats del /home [IMG]http://ubuntuforums.org/picture.php?albumid=2503&pictureid=8493[/IMG]
(què vol dir això "(part del contingut és il·legible)")?

i 3,2 segons df -h

[email]joan@joan-laptop:~/.local[/email]/share/Trash/info$ df -h
S. fitxers      Mida En ús Lliure  %Ús Muntat a
/dev/sda6        37G   16G    20G  45% /
udev            2,0G  4,0K   2,0G   1% /dev
tmpfs           791M  908K   791M   1% /run
none            5,0M     0   5,0M   0% /run/lock
none            2,0G  152K   2,0G   1% /run/shm
/dev/sda7       201G  187G   3,2G  99% /home
[email]joan@joan-laptop:~/.local[/email]/share/Trash/info$

---

### Post by jinglada on 2012-10-01
> **ffp said:**
> 
Et funciona el Psensor? si et funciona no cal que instalis res mes ! 

Crec que si. Tanmateix el ventilador s'engega indiferentment de que les temperatures del Psensor siguin les temperatures límit o no.

[IMG]http://ubuntuforums.org/picture.php?albumid=2503&pictureid=8494[/IMG]

---

### Post by wgarcia on 2012-10-01
Continuo pensant que el ventilador que sents és el de la targeta gràfica i no el dels processadors, i no s'apaga perquè no tens el controlador adequat per a la targeta gràfica que tens. 

No sé gaire de targetes ATI Radeon com la que tens, mai no he tingut una targeta d'aquest tipus, però potser ens està llegint algú que tingui més experiència amb aquestes targetes. Sé que hi ha un controlador lliure que es diu Catalyst i controladors propietaris, o Catalyst és el propietari, potser canviant el controlador s'arregla aquest problema.

---

### Post by jinglada on 2012-10-01
> **wgarcia said:**
> Continuo pensant que el ventilador que sents és el de la targeta gràfica i no el dels processadors, i no s'apaga perquè no tens el controlador adequat per a la targeta gràfica que tens. 

No sé gaire de targetes ATI Radeon com la que tens, mai no he tingut una targeta d'aquest tipus, però potser ens està llegint algú que tingui més experiència amb aquestes targetes. Sé que hi ha un controlador lliure que es diu Catalyst i controladors propietaris, o Catalyst és el propietari, potser canviant el controlador s'arregla aquest problema.

Hola wgarcia. Hast vist el segon post previ al que em respons? Em sembla que ja està arranjat el tema del ventilador, oi?

T'agrairia també si em pots dir res respecte a l'altre post següent, o sigui al penúltim dels que he enviat jo. Gràcies!

---

### Post by wgarcia on 2012-10-01
No, no l'havia vist... És que en aquest fil hi ha tants problemes diferents que costa (almenys a mi) de seguir.

O sigui que ara el que falta és aclarir només allò del "contingut il·legible? A mi em sembla que això el més probable és que siguin carpetes o fitxers on el teu usuari no té permís de lectura, per exemple carpetes o fitxers de sistema.

---

### Post by jinglada on 2012-10-03
> **jinglada said:**
> Hi ha alguna manera de detectar els fitxers creats automàticament o involuntàriament en el /home a partir d'una data determinada?

Després d'esborrar els 5 GiB del /home/.Trash-0 (que tenien dates des del 2009 fins el març 2012) em va donar que em quedaven 3,2 GiB lliures. On van anar a parar els 1,8 restants?

He trobat el comandament "find" per a cercar els fitxers creats o modificats entre dues dates determinades i ja que vaig actualitzar el dia 29/9, o sigui ara fa 4 dies, he fet:

joan@joan-laptop:~$ find -mtime -3 -mtime -4

i he trobat el següents directoris i fitxers creats o modificats entre el 29/9 i l'endemà, entre el quals els més voluminosos són:

/home/joan/.cache amb 5,6 GiB dels quals:
/home/joan/.cache/tracker amb 3,8 GiB
/home/joan/.cache/spotify amb 1,0 GiB (reinstal·lat després de l'actuaització al 12.04 LTS)

i a més

/home/joan/.config amb 544,9 MiB
/home/joan/.beagle amb 531,2 MiB

Pot ser que el **tracker** fos el causant de la reducció d'espai lliure?

He decidit eliminar el **Tracker** i el directori /home/joan/.cache/tracker i he recuperat 4 GiB. Per cercar fitxers uso el **Catfish** amb opció ***find*** i em va prou bé!

---

