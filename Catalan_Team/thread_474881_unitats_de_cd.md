---
title: "unitats de cd"
date: 2007-06-15
forum: Catalan Team
---

### Post by utep on 2007-06-15
Al marge de la desesperació!!!

No fa gaire que tinc UBUNTU i tins un merder de unitats impresionant i, a més ara, no em llegeig els cds...
Avere si algú em pot ajudar..
El hardware que tinc realment es el següent:
- Disc dur amb varies particions (1 per WIN, 2 per UBUNTU - kernel i swap-, 1 gran d'uns 56 GB)
- Lector DVD
- Grabador CD
- Grabador DVD

i res més

Tanmateix, m'apareix a "ordinador totes aquestes unitats:

[IMG]http://img388.imageshack.us/img388/7508/capturach4.png[/IMG]

a més, no em llegeig ni cd ni dvd en cap de les unitats apareixent-me els errors següents: 

CD-ROM 1: No s'ha pogut muntar el volum seleccionat --> mount: special device /dev/hdd does not exist

CD-ROM 1: No s'ha pogut muntar el volum seleccionat --> mount: special device /dev/hdb does not exist

CD-ROM 1: No s'ha pogut muntar el volum seleccionat --> mount: special device /dev/hdc does not exist

Unitat CD-ROM/DVD-ROM: No es pot muntar el medi

Unitat CD-RW: No es pot muntar el medi

Unitat CD-RW/DVD+-RW: No es pot muntar el medi

Defet, al principi de instalar-me el UBUNTU, a "ordinador" m'apareixien les unitats CD-ROM 1, CD-ROM 2 i CD-ROM 3 però quan introduir un cd a qualsevol de les unitats, m'apareixia una quarta unitat desde on podia veure els arxius....Ara en canvi, apareixen a simple vista totes les unitats i no em llegeix cap cd... :(

Per si serveix d'ajuda, copio el arxiu fstab que tinc:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=fb8911c7-8906-4725-8e89-687c962b5845 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=5442397d-d470-4f23-8606-782c03d42447 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Moltes gràcies per anticipat!

Salut,
utep

---

### Post by AlexMuntada on 2007-06-16
Ens seria molt útil saber quina versió d'Ubuntu teniu instal·lada i si la teniu actualitzada.  També ho seria que ens mostreu el resultat d'executar això:
```
dmesg | grep -i cdrom
```

---

### Post by utep on 2007-06-18
Merci Alex,

T'explico:
- Tinc la versió 7.04
- No tenia cap actualització instalda aixi que quan m'ho has dit he instalat les 56 actualitzacions que tenia pendents d'instalar
- Al reiniciar l'ordinador despres d'actualitzar-lo, m'apareix la possibilitata de iniciar amb aquestes les versions: 2.6.20-16 i 2.6.20-15, tot i aixi, al iniciar amb la versió 2.6.20-16 m'apareix l'error:

*************
Starting up...

crc error

--System halted
**************
I el pc es queda penja i l'haic de reiniciar manualment
Per tant només puc iniciar amb la 2.6.20-15

- Pel que fa al comando **dmesg | grep -i cdrom** que m'has comentat, no fa absolutament res! no surt cap resultat...

...Ara no se si estic millor o pitjor que abans.... AJUDA!


Salut,
utep

---

### Post by papapep on 2007-06-18
Prova ficant-hi un guió:

dmesg | grep -i cd-rom

---

### Post by utep on 2007-06-18
merci papapep, em surt això:

[   36.190952] scsi 0:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8526B  1.04 PQ: 0 ANSI: 5
[   36.194092] scsi 1:0:0:0: CD-ROM            SONY     DVD-ROM DDU1621  S3.1 PQ: 0 ANSI: 5
[   36.197618] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[   36.319057] Uniform CD-ROM driver Revision: 3.20
[   36.319348] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   36.322083] sr 1:0:0:0: Attached scsi CD-ROM sr1
[   36.339421] sr 1:0:1:0: Attached scsi CD-ROM sr2


que defet no entenc res però veic no se què scsi per aqui al mig i bueno, més que res comentar que no tinc res scsi...

---

### Post by AlexMuntada on 2007-06-18
> **utep said:**
> al iniciar amb la versió 2.6.20-16 m'apareix l'error:

*************
Starting up...

crc error

--System halted
**************
I el pc es queda penja i l'haic de reiniciar manualment
Per tant només puc iniciar amb la 2.6.20-15

La versió 2.6.20-16 està donant força maldecaps... :/

Assegureu-vos que teniu aquests paquets instal·lats:
```
$ dpkg -l linux-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-...
$ dpkg -l linux-restricted-modules-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-restricted-modules-...
```

En cas que no els tingueu, els hauríeu d'instal·lar:
```
sudo apt-get install linux-$(uname -r|cut -f3 -d-)
sudo apt-get install linux-restricted-modules-$(uname -r|cut -f3 -d-)
```

Si amb això segueix fallant el nucli 2.6.20-16, aviseu-nos i seguirem
provant més coses.

---

### Post by utep on 2007-06-18
Alexmuntada, pel que veic ja ho tinc instalat:

tep@tep-desktop:~$ dpkg -l linux-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-generic  2.6.20.16.28.1 Complete Generic Linux kernel
tep@tep-desktop:~$ dpkg -l linux-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-generic  2.6.20.16.28.1 Complete Generic Linux kernel

---

### Post by AlexMuntada on 2007-06-18
El segon paquet era: ```
dpkg -l linux-restricted-modules-$(uname -r|cut -f3 -d-) | grep ^i
```

---

### Post by utep on 2007-06-18
tb està instalat:

dpkg -l linux-restricted-modules-$(uname -r|cut -f3 -d-) | grep ^i
ii  linux-restricted-modules-generic 2.6.20.16.28.1 Restricted Linux modules for generic kernels




(bueno, jo vaic dient que tot això està instalat però no ho se suposo que quan posa ii linux..... vol dir que ja està instalat... tu sabras millor que jo...

Soc una mica novato amb el tema...

Merci per la paciencia, alex

---

### Post by AlexMuntada on 2007-06-18
Seguint amb el tema del CRC error, podria ser que tingueu un problema a l'initramfs.

Proveu d'executar això a veure si millora l'arrencada amb el 2.6.20-16 (haureu de reiniciar quan hagi acabat):
```
sudo update-initramfs -c -k 2.6.20-16-generic
```

---

### Post by AlexMuntada on 2007-06-18
Quant al tema de les unitats, executeu això i indiqueu-nos el resultat:
```
lshal | egrep '(^udi =|block\.device|linux\.sysfs_path)' | egrep -C1 "/dev/(scd|hd[a-z])'"
```

---

### Post by utep on 2007-06-18
:(:(:(:(:(

> **AlexMuntada said:**
> Seguint amb el tema del CRC error, podria ser que tingueu un problema a l'initramfs.

Proveu d'executar això a veure si millora l'arrencada amb el 2.6.20-16 (haureu de reiniciar quan hagi acabat):
```
sudo update-initramfs -c -k 2.6.20-16-generic
```

Pel que fa a l'error crc, continua igual, He executat el que m'has dit i llavors al reiniciar he intentat iniciar dos cops amb 2.6.20-16 generic i una amb recovery mode i amb totes m'ha sortit el mateix error que abans..
Inclus al provar per primera vegada tornar a iniciar amb 2.6.20-15 també m'ha posat el mateix error; al iniciar per segona vegada amb el 15 ha iniciat be... (tampoc es la primera vegada que el 15 em fot el susto amb aquest error tot i que no li vaic donar importancia, va ser abans de instalar les actualitzacions)

> **AlexMuntada said:**
> Quant al tema de les unitats, executeu això i indiqueu-nos el resultat:
```
lshal | egrep '(^udi =|block\.device|linux\.sysfs_path)' | egrep -C1 "/dev/(scd|hd[a-z])'"
```

He executat aquest comando i no fa res no se si potser t'hauràs deixat algun signe... amb tants simbols raros.... (defet a mi tot em sona a xino) --mica en mica vaic pillant algo tot i aixi-)

---

### Post by AlexMuntada on 2007-06-19
> **utep said:**
> Pel que fa a l'error crc, continua igual...
Inclus al provar per primera vegada tornar a iniciar amb 2.6.20-15 també...
(tampoc es la primera vegada que el 15 em fot el susto amb aquest error
tot i que no li vaic donar importancia

Podria tractar-se d'un problema de memòria: hauríeu d'executar el test
de memòria que hi ha als CD d'instal·lació d'Ubuntu.  Deixeu-lo executar
durant 3-4 passades perquè els errors no sempre són deterministes.

> He executat aquest comando i no fa res

Cert, calia refinar una mica més les expressions regulars i corregir un petit error:
```
lshal | egrep '(^udi =|block\.device|linux\.sysfs_path)' | egrep -C1 "/dev/(scd|[hs]d[a-z]')"
```

---

### Post by utep on 2007-06-19
> **AlexMuntada said:**
> Podria tractar-se d'un problema de memòria: hauríeu d'executar el test
de memòria que hi ha als CD d'instal·lació d'Ubuntu.  Deixeu-lo executar
durant 3-4 passades perquè els errors no sempre són deterministes.

M'hauries d'explicar una mica més com fer aquest test de memoria. Cal iniciar l'ordinador amb el cd? es pot trobar lo del test buscant per les carpetes del cd? Em podries dir exactament els passos a seguir? i amb les pantalles que em trobaré?

> **AlexMuntada said:**
> ```
lshal | egrep '(^udi =|block\.device|linux\.sysfs_path)' | egrep -C1 "/dev/(scd|[hs]d[a-z]')"
```

Al executar això m'ha sortit el resultat següent:
>  lshal | egrep '(^udi =|block\.device|linux\.sysfs_path)' | egrep -C1 "/dev/(scd|[hs]d[a-z]')"
udi = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_H42N'
  block.device = '/dev/scd2'  (string)
  linux.sysfs_path_device = '/sys/block/sr2'  (string)
--
udi = '/org/freedesktop/Hal/devices/storage_model_DVD_ROM_DDU1621'
  block.device = '/dev/scd1'  (string)
  linux.sysfs_path_device = '/sys/block/sr1'  (string)
--
udi = '/org/freedesktop/Hal/devices/storage_model_CD_RW_GCE_8526B'
  block.device = '/dev/scd0'  (string)
  linux.sysfs_path_device = '/sys/block/sr0'  (string)
--
udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380021A_3HV3XJ6X'
  block.device = '/dev/sda'  (string)
  linux.sysfs_path_device = '/sys/block/sda'  (string)


Tot i així, de forma efectiva no he observat canvis.
Ara però a diferència del primer post em llegeix els cd, tot i que ja mels llegia abans d'executar aquesta última instrucció; crec que els he pogut començar a llegir despres d'alguna reiniciada que he fet i de forma miraculosa...
Indicar també que si mires la foto de la pantalla que he penjat al inici d'aquest post, desde "ordinador" apareixen 6 unitats i desde "llocs" a l'esquerra de la finestra apareixen només 3 (CD-ROM 1, CD-ROM 2 i CD-ROM 3). Alhora d'introduir un cd, a "ordinador" de les 6 unitats, la corresponent al cd que introdueixo (que mai son CD-ROM 1, CD-ROM 2 o CD-ROM 3) canvia d'icona amb el que correspon al cd en qüestió. Pel que fa a "llocs" a l'esquerra de la pantalla, n'apareix una quarta amb l'icona corresponent.
- No se pq apareix aquesta diferència de continguts sengons com ho consultis
- Ara com et comen-t'ho puc treballar amb un cd però el problema principal però es que apareixen les 3 unitats fantasmes CD-ROM 1, CD-ROM 2 i CD-ROM 3...

Merci per tot,
utep

---

### Post by AlexMuntada on 2007-06-19
> **utep said:**
> M'hauries d'explicar una mica més com fer aquest test de memoria. Cal iniciar l'ordinador amb el cd? es pot trobar lo del test buscant per les carpetes del cd?

És molt senzill: només cal iniciar l'ordinador amb el CD i triar l'opció del test de memòria enlloc del d'instal·lar l'Ubuntu.  La resta, funciona tot solet, si no recordo malament. ;-)

> **utep said:**
> Al executar això m'ha sortit el resultat següent

L'ordre que us havia indicat no efectua cap canvi al sistema, només ens proporciona informació d'utilitzat per veure com es detecten les unitats de CD.  En aquest cas, es pot veure que les unitats de CD són:
[LIST]
[*]/dev/scd0 (CD_RW)
[*]/dev/scd1 (DVD_ROM)
[*]/dev/scd2 (DVDRAM)
[/LIST]

Així doncs, hauríeu de canviar les entrades dels CD al fstab que teniu així:
```
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom2 udf,iso9660 user,noauto 0 0
```

La idea seria canviar **hdd** per **scd0**, **hdb** per **scd1** i **hdc** per **scd2**, però abans seria interessant saber quins enllaços simbòlics ha creat el sistema:
```
ls -l /dev | grep scd
```

Si és possible tenir un enllaç diferent per a cada unitat, aleshores serà millor indicar els enllaços al **fstab**.  D'aquesta manera, no us haureu de preocupar de com s'assignen les unitats al nucli perquè els noms simbòlics del **fstab** no canviaran.

> **utep said:**
> Ara però a diferència del primer post em llegeix els cd, tot i que ja mels llegia abans d'executar aquesta última instrucció

Això pot ser degut a les actualitzacions que us faltaven.

> **utep said:**
> No se pq apareix aquesta diferència de continguts sengons com ho consultis

Malauradament, jo tampoc.  A veure si amb el canvi que proposo al **fstab** funciona.

---

### Post by utep on 2007-06-19
Anem a veure:

Pel que fa a lo de lesunitats de CD, perdfecte!!! he seguit les teves indicacions i tema solucionat!!
Per fi han desaparegut les tres unitats fantasmes CD-ROM 1 2 i 3!!

Tot i així, les tres unitats restants (les bones) desde "ordinador" es veueen les tres però desde el menu de l'esquerra només es veu aquella unitat que te un cd dins...però bueno això ja es per ser més tikis-mikis...

Moltes gracies per aquest tema!!

Pe que fa a l'error CRC he provat de fer el memory test tal i com m'has dit i després d'una sola pasada, la versió 16 no funcionava i la 15 si. Llavors he tornat a llegir el teu post on deies que li fés unes cuantes passades; doncs be com que he vist que era una mica llarg (algo més de 15min per passada) i havia de marxar, he decidit deixant-lo fent passades tota la tarda.
Despres de 27 passades i mitja, ara ja no puc iniciar l'ubuntu ni desde la versió 15 ni desde la 16 ja que m'apareix el mateix error en ambdues versions!!! :(:(:(:(:( inclús amb una de les reiniciades que he fet intentant-ho, abans de sortir el menu on tries la versió m'ha sortit un missatge de "Memory test error" o quelcom similar on havia de premer f1 per continuar i que m'aparagués el menu a triar...(no se si te algo a veure o et pot ajudar...)
Ara he hagut d'iniciar amb windows per poder escriure això!!

...Espero les teves noticies!

(i jo que em pensava que el ubuntu no es penjava mai ak revés del windows!!:p:p)

---

### Post by papapep on 2007-06-19
Axioma: "Linux mai es penja" 

Demostració: Tu tens un problema de RAM, no de sistema operatiu :-P

---

### Post by utep on 2007-06-19
> **papapep said:**
> Axioma: "Linux mai es penja" 

Demostració: Tu tens un problema de RAM, no de sistema operatiu :-P

La teva demostració es poc riguros en la mida que no has tingut en compte que el windows em funciona correctament sense cap problema.
A més no li trobo molt sentit el fet que una versió funcioni i l'altre no; és més, que a vegades funcioni i avegades no...
Si la Ram esta trencada està trencada a tots els efectes!! no arrencaria el xindows tampoc, no?

Vamos, no domino gaire.. però a primera vista ho veic així...

Defet el teu post m'ha fet molta gracia; a més em moro de ganes t'explicare un acudit que m'ha vingut al cap amb la teva resposta que si no el dic, revento!

> Un dictaddor esta fent un discurs i diu a la gent: 
- Des que jo estic al poder, ningú no s'ha anat al llit sense sopar!!
...i salta un d'entre el public i li diu: - Colti! que jo no he sopart avui
i el dictador li respon: - No ha sopat? doncs avui no dorm!

:D:D:D:D

---

### Post by AlexMuntada on 2007-06-19
> **utep said:**
> Pel que fa a lo de lesunitats de CD, perdfecte!!! he seguit les teves indicacions i tema solucionat!!

De fet, no les heu seguit pas perquè jo us he demanat que abans de fer el canvi m'enviéssiu la sortida de l'ordre **ls -l /dev | grep scd** i no ho heu fet. :(

El problema amb què us podeu trobar és que canviï el nom de les unitats de CD i us deixaran de funcionar un altre cop, per això us demanava un pas addicional per mirar d'evitar aquest possible problema.

> **utep said:**
> desde el menu de l'esquerra només es veu aquella unitat que te un cd dins

Aquest és el comportament normal.

> **utep said:**
> m'ha sortit un missatge de "Memory test error" o quelcom similar

Així doncs, no hi ha dubte que teniu problemes de memòria.

> **utep said:**
> Ara he hagut d'iniciar amb windows per poder escriure això!!

Algunes versions del Finestres no saben aprofitar tota la memòria disponible; potser aquesta és la diferència, però no vol dir que la culpa sigui de l'Ubuntu. El que heu de fer és canviar la memòria. ;)

---

### Post by utep on 2007-06-19
> **AlexMuntada said:**
> Algunes versions del Finestres no saben aprofitar tota la memòria disponible; potser aquesta és la diferència, però no vol dir que la culpa sigui de l'Ubuntu. El que heu de fer és canviar la memòria. ;)

Suposem dopncs que el problema es sols la meva ram i que no haurà afectat al dics dur ni res més, no? canvio la Ram i llestos! Ha de ser alguna ram especial? marca, caracteristiques; ho dic pq no em torni a passar!! pq defet, hi ha alguna explicació lògica de perquè passa?

¡¡¡Però si jo vaic optar per passarme a ubuntu, entre d'altres coses pq era gratis!!!

Ja m'ho deia el meu avi, sempre has de llegir la lletra petita!!

p.d. Continuo desconcertat amb lo dels teorics problemes de memoria segons el raonament que li he fet al papapep...però bueno..

---

### Post by AlexMuntada on 2007-06-19
> **utep said:**
> Suposem dopncs que el problema es sols la meva ram i que no haurà afectat al dics dur ni res més, no? canvio la Ram i llestos!

En principi sí, però tan sols és la meva opinió basada en les dades que tinc disponibles.

> Ha de ser alguna ram especial? marca, caracteristiques

Ni idea, això ho podeu esbrinar mirant el model de la placa base. També pot ser que només falli 1 dels mòduls de memòria si en teniu més d'1 o que el problema sigui més greu del que sembla i finalment no sigui la memòria sinó la placa base.

Si teniu més d'1 mòdul de memòria, jo començaria provant de treure'n 1 i treballar només amb els restants, de forma que els proveu tots i pugueu determinar quins fallen. Un cop fet això o si només en teniu 1, mireu d'aconseguir-ne un altre de les mateixes característiques per tal de provar-lo abans de comprar-lo.

> hi ha alguna explicació lògica de perquè passa?

Si resulta que l'error és de memòria, aquestes coses passen i els motius poden ser diversos: errades durant el procés de fabricació, canvis bruscos de temperatura, manipulació indeguda, talls de corrents sobtats, etc. Tot el maquinari pot tenir errors.

> Continuo desconcertat amb lo dels teorics problemes de memoria segons el raonament que li he fet al papapep...però bueno..

És ben senzill: imaginem que teniu 2 mòduls de 256MB. Si l'error està en el segon mòdul (256-512MB) i el Finestres només utilitza el primer (0-256MB), és normal que no us doni cap problema (aparentment).

Penseu què és pitjor... que us avisin de què us falla la memòria i no pugueu usar el PC o que no us avisin, utilitzeu el PC sense saber-ho i acabeu perdent dades per aquest motiu?

---

### Post by lpargemi on 2007-09-25
Hola

Vet aquí que jo apareixo uns mesos després, i tinc el mateix problema que n'Utep amb el CRC

Vaig instal.lar l'Ubuntu 7.04, i quan vaig haber configurat la xarxa i el suport per a idiomes, el sistema em va dir que tenia 159 (o així)  actualitzacions pendents i que em recomanaven fer-les.

Vaig fer-les, i des d'aleshores em passa el mateix amb el CRC: No arrenca amb la versió 16, però si amb la 15. (I a més suposo que la 15 deu tenir les actualitzacions ja fetes, perquè ara només em diu que en tinc dues pendents).

Abans d'escriure he fet les proves que comenta l'Àlex, i en principi em diu que esta bé.

Per si serveix de pista, aquestes dues actualitzacions fallen cada vegada, donant el seguent log

[I][INDENT]E: /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.32_i386.deb: sistema de fitxers de l'arxiu tar corrupte - arxiu del paquet corrupte
E: /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.32_i386.deb: sistema de fitxers de l'arxiu tar corrupte - arxiu del paquet corrupte


.. i és que la corrupció arriba a tot arreu
[/INDENT][/I]

Us ho envio per veure si algú sap com he de solucionar-ho.

Salut

Lluís

---

### Post by AlexMuntada on 2007-09-29
Com ja deveu haver llegit, el problema del CRC en papapep i jo l'hem atribuït a la memòria.

D'altra banda, si voleu resoldre el problema amb els paquets corruptes hauríeu d'executar això (assegureu-vos també que teniu prou espai disponible a /var):

```
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get install -f
```

A partir d'aleshores, les actualitzacions us haurien de funcionar correctament.

---

### Post by lpargemi on 2007-09-29
Doncs en el meu cas la memòria no deu ser.

Es va passar tota la nit fent el test que s'engega des del grub, i no va donar cap errada.

Una altra cosa és que n'hi hagi poca: tinc només 256 Mb... però en principi era suficient.

Lluís

---

### Post by shimoda on 2007-10-27
Doncs des que vaig actualitzar a la 7.10 a mi també m'apareixia una misteriosa "CD-ROM 1". 

Gràcies a aquest post ho he arreglat...

merci!!! :biggrin:

---

