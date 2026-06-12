---
title: "Sant-tornem-hi: GRUB i Windows7"
date: 2011-11-15
forum: Catalan Team
---

### Post by Joan Marc on 2011-11-15
Hola,
Primer de tot sé que és un tema super parlat, discutit i arreglat al fòrum, però m'està passant una cosa molt extranya.
Al PC tenia fins fa uns dies, el Windows7 que venia d fabrica, i l'Ubuntu 11.04. Vaig decidir-me a reinstal·lar el W7 ja que el pobre ja feia pena, i, com ja m'esperaba, el GRUB va desaparèixer. 
Així que he arrancat amb un LiveCD, i obert un terminal, per fer un "sudo fdisk -l", amb aquests resultats:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1f24c2c4

   Device Boot      	Start		End		Blocks   	Id  	System
/dev/sda1   *           1          	26      	203776    	7  	HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            	26       	50645  	        406593536    	7 	HPFS/NTFS
/dev/sda3           	50645       	59116    	68046849    	5 	Extended
/dev/sda4          	59116      	60802    	13539328   	7  	HPFS/NTFS
/dev/sda5           	58598       	59116     	4159488   	82  	Linux swap / Solaris

```
Com podeu veure, no n'hi ha cap que posi "Linux", però sé del cert, que el tinc instal·lat al /dev/sda3, tot i que posa "Extended".
Intento fer el pas següent, però em surt error:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: you must specify the filesystem type

```
I aquí em quedo... Què l'hi ha passat a la partició on tinc l'Ubuntu?
Gràcies!

---

### Post by wgarcia on 2011-11-18
Te'n recordes quin era el tipus de sistema de fitxer que tenies? (Si era una instal·lació recent de Linux seria "ext4", si és més antiga hi ha la possibilitat que sigui "ext3").

Si és "ext4" per exemple, pots provar:

```
mount -t ext4 /dev/sda3 /mnt
```

---

### Post by Joan Marc on 2011-11-18
> **wgarcia said:**
> Te'n recordes quin era el tipus de sistema de fitxer que tenies? (Si era una instal·lació recent de Linux seria "ext4", si és més antiga hi ha la possibilitat que sigui "ext3").

Si és "ext4" per exemple, pots provar:

```
mount -t ext4 /dev/sda3 /mnt
```
Sí, és bastant recent, així que he provat amb ext4:
```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
No li he fet cas, i he provat amb "gksudo", i almenys, ha fet alguna cosa diferent:
```
ubuntu@ubuntu:~$ gksudo mount -t ext4 /dev/sda3 /mnt
ubuntu@ubuntu:~$

```
Però quan he intentat continuar:
```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$

```
I aquí em quedo... Si és molt complicat, instal·lo l'Ubuntu 11.10 fent una instal·lació nova, i santes pasques (no hi tinc cap document important al 11.04).
Merci per contestar!

---

### Post by wgarcia on 2011-11-18
Tens un directori anomenat "/mnt" al directori root "/" ?

---

### Post by Joan Marc on 2011-11-18
Doncs ni idea, jo tan sols estava seguint els manuals que he trobat per la web:
[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)
[http://www.noticiasubuntu.com/reinstalar-grub-2-despues-de-instalar-windows-7/](http://www.noticiasubuntu.com/reinstalar-grub-2-despues-de-instalar-windows-7/)
...
També he trobat aquest altre:
[http://cmt.lugcix.org/?p=424](http://cmt.lugcix.org/?p=424)
Però no entenc a què es refereix, a l'apartat 3, quan diu "substituïr /dev/sda pel disc en el qual vols instal·lar el GRUB", així que no l'he provat.

---

### Post by wgarcia on 2011-11-19
Fixa't si tens aquest directori "/mnt" perquè si no el tens la instrucció "mount" que menciones no funcionarà. 

Per veure si tens aquest directori fes simplement des de la terminal:

```
ls /
```

i t'hauria de sortir una llista de directoris entre els quals hauries de veure "mnt".

---

### Post by Joan Marc on 2011-11-19
Sí, sí que hi és:

```
ubuntu@ubuntu:~$ sudo ls /
bin   cdrom  etc   initrd.img  media  opt   rofs  sbin	   srv	tmp  var
boot  dev    home  lib	       mnt    proc  root  selinux  sys	usr  vmlinuz
ubuntu@ubuntu:~$
```
Ara bé, /mnt/dev no existeix:
```
ubuntu@ubuntu:~$ sudo ls /mnt/dev
ls: cannot access /mnt/dev: No such file or directory
```
M'he fixat que existeix /dev, i m'ha sortit això:
```
ubuntu@ubuntu:~$ sudo ls /dev
autofs		 mapper		     sda2      tty27  tty60	 ttyS7
block		 mcelog		     sda3      tty28  tty61	 ttyS8
bsg		 mem		     sda4      tty29  tty62	 ttyS9
btrfs-control	 net		     sda5      tty3   tty63	 uinput
bus		 network_latency     sdb       tty30  tty7	 urandom
cdrom		 network_throughput  sdb1      tty31  tty8	 usbmon0
cdrw		 null		     sg0       tty32  tty9	 usbmon1
char		 oldmem		     sg1       tty33  ttyprintk  usbmon2
console		 pktcdvd	     sg2       tty34  ttyS0	 usbmon3
core		 port		     shm       tty35  ttyS1	 usbmon4
cpu		 ppp		     snapshot  tty36  ttyS10	 usbmon5
cpu_dma_latency  psaux		     snd       tty37  ttyS11	 usbmon6
disk		 ptmx		     sr0       tty38  ttyS12	 usbmon7
dri		 pts		     stderr    tty39  ttyS13	 usbmon8
dvd		 ram0		     stdin     tty4   ttyS14	 v4l
dvdrw		 ram1		     stdout    tty40  ttyS15	 vcs
ecryptfs	 ram10		     tty       tty41  ttyS16	 vcs1
fb0		 ram11		     tty0      tty42  ttyS17	 vcs2
fd		 ram12		     tty1      tty43  ttyS18	 vcs3
freefall	 ram13		     tty10     tty44  ttyS19	 vcs4
full		 ram14		     tty11     tty45  ttyS2	 vcs5
fuse		 ram15		     tty12     tty46  ttyS20	 vcs6
fw0		 ram2		     tty13     tty47  ttyS21	 vcs7
hidraw0		 ram3		     tty14     tty48  ttyS22	 vcs8
hpet		 ram4		     tty15     tty49  ttyS23	 vcsa
input		 ram5		     tty16     tty5   ttyS24	 vcsa1
kmsg		 ram6		     tty17     tty50  ttyS25	 vcsa2
lirc0		 ram7		     tty18     tty51  ttyS26	 vcsa3
log		 ram8		     tty19     tty52  ttyS27	 vcsa4
loop0		 ram9		     tty2      tty53  ttyS28	 vcsa5
loop1		 random		     tty20     tty54  ttyS29	 vcsa6
loop2		 rfkill		     tty21     tty55  ttyS3	 vcsa7
loop3		 rtc		     tty22     tty56  ttyS30	 vcsa8
loop4		 rtc0		     tty23     tty57  ttyS31	 vga_arbiter
loop5		 scd0		     tty24     tty58  ttyS4	 video0
loop6		 sda		     tty25     tty59  ttyS5	 zero
loop7		 sda1		     tty26     tty6   ttyS6
ubuntu@ubuntu:~$

```
Es veu que existeix, entre molts altres, /dev/sda3.
Ho he de montar aquí?

Moltes gràcies!

---

### Post by wgarcia on 2011-11-19
Doncs sí que tens el directori "mnt". En quant a "dev" és un dispositiu virtual on es munten diverses parts del sistema de forma automàtica.

Al següent missatge:

[http://ubuntuforums.org/showpost.php?p=11083289&postcount=2](http://ubuntuforums.org/showpost.php?p=11083289&postcount=2)

hi ha una explicació sobre com generar un fitxer on es pot veure bé la disposició de les teves particions i què tens a cada una, pot ser útil per veure perquè no et deixa acabar de muntar l'Ubuntu.

---

### Post by Joan Marc on 2011-11-19
Així ho he fet. T'adjunto el document "RESULTS.txt" a veure què hi pots veure.
Pel que jo he vist i puc entendre, ha de ser la partició sda3 per nassos ja que a sda1 hi ha algo de "SYSTEM", a la sda2 tinc el W7, sda4 tinc coses del "Recovery" del PC, i a la sda5 hi ha el Swap del Linux, per tant, només queda la sda3.
Com ho veus?

Gracies de nou.

---

### Post by wgarcia on 2011-11-19
Ara es veu clar, crec, tot que ja es veia al teu primer "fdisk". 

Als discos (per raons històriques) sols poden haver-hi 4 particions primàries, però una d'elles pot ser una partició extensa, i dins d'una partició extensa es poden crear particions lògiques, tantes com es vulgui. 

En el teu sistema /dev/sda3 és una partició extensa, és per això que no es pot muntar, perquè una partició extensa és simplement un contenidor que no té cap tipus de sistema de fitxers. 

Dins de la teva partició extensa es pot veure la partició lògica /dev/sda5, la partició "swap" o d'intercanvi, i un espai sense assignar que sembla que és on tenies el teu arrel de Linux. Sembla que aquesta partició lògica l'ha destruït la instal·lació de Windows. 

En principi la informació que tenies deu estar tota encara aquí, i seria possible de recuperar, però si com dius

> Si és molt complicat, instal·lo l'Ubuntu 11.10 fent una instal·lació nova, i santes pasques (no hi tinc cap document important al 11.04).

potser no val la pena perquè dóna feina fer-ho. En aquest cas sols es tracta de reinstal·lar Ubuntu a aquesta partició lògica /dev/sda3, creant aquí dins les carpetes que vulguis.

Una altra observació és que quasi tot l'espai el tens assignat a les particions que tenen Windows, podries reduir l'espai d'una d'elles, per exemple /dev/sda2 i reassignar-lo a /dev/sda3, perquè sinó et quedaràs sense espai força aviat a Ubuntu. Si fas això convé desar totes les dades i defragmentar un parell de cops la partició de Windows que vols reduir de grandària.

---

### Post by Joan Marc on 2011-11-19
Ok, dons instal·laré el 11.10 que de fet ja ho volia fer.
Lo que dius de re-assignar l'espai, bé, ara em titllareu de botifler, però el cert és que l'Ubuntu només el faig servir quan vull fer alguna "tonteria" i  anar ràpid o quan el Windows decideix fer vaga i no engegar, per tant, per l'ús que l'hi he de donar, crec que l'espai ja el tinc ben distribuït (fins i tot crec que me'n sobra jeje).

wgarcia, moltes gràcies per la teva ajuda i el teu temps :):)

---

### Post by wgarcia on 2011-11-19
Doncs perfecte, si has pagat pel Windows millor que el facis servir, que no es tracta de llençar el diners amb el temps que corren :wink:

---

### Post by Joan Marc on 2011-11-19
> **wgarcia said:**
> Doncs perfecte, si has pagat pel Windows millor que el facis servir, que no es tracta de llençar el diners amb el temps que corren :wink:
Pagar pel Windows? Què és això? xD
No el faig servir més perquè l'hagi pagat o no, el faig servir per poder fer córrer decentment l'AutoCAD, SolidWors, per poder programar i compilar amb C++ sense deixar-m'hi la pell i per suposat, per jugar. Crec que els dos SO es diferencien molt, cadascun té els seus punts forts, i jo intento aprofitar-los combinant els dos. :)

---

### Post by wgarcia on 2011-11-19
El que em referia és que si el Windows et fa servei i o bé l'has pagat en comprar l'ordinador, o no tens problema amb piratejar-lo, no hi ha cap raó per no fer-lo servir. 

Almenys per a mi Linux no és una religió, és una tecnologia amb la qual m'agrada treballar i amb la qual puc fer tota la meva feina i una part del meu oci (no faig Autocad però, ni sé si hi ha bones alternatives lliures o comercials a linux).

En quant a programació sí que no canviaria Linux per res.

Tampoc jugo amb l'ordinador, cosa que també entenc que pot ser una bona raó per mantenir una instal·lació de Windows. De totes maneres els jocs a linux s'estan desenvolupant ràpidament, una de les novetats recents interessants és l'accés a Desura, un client de jocs que porta molts jocs diferents:

[http://www.desura.com/](http://www.desura.com/)

---

### Post by Joan Marc on 2011-11-20
Totalment d'acord amb tu amb les dues primeres línies
> **wgarcia said:**
> En quant a programació sí que no canviaria Linux per res.

Amb això també tens raó, però a mitges. Em refereixo a que estic segur que es pot programar sense cap problema amb C++ a l'Ubuntu, però a data d'avui, he estat incapaç de trobar un programa que s'assembli en quant a facilitat de funcionament, al Dev-C++ que faig servir amb Windows... si en saps algun em faries un gran favor!

Lo dels jocs, no he provat el Desura, però els pocs jocs que he provat son bastant pobres, per dir-ho d'alguna manera.

---

### Post by wgarcia on 2011-11-20
Hi ha molts entorns, jo no sóc programador professional i sóc una mica vell, vinc del món d'Unix, així que per al parell de projectes on participo faig servir coses com "emacs" com a editor/entorn de programació i ja m'és suficient. 

Però òbvimament hi ha molts IDE lliures a Linux, aquí es pot trobar referències a uns quants:

[https://help.ubuntu.com/community/PowerUsersProgramming](https://help.ubuntu.com/community/PowerUsersProgramming)

Un entorn del qual he sentit parlar molt bé és:

[http://www.codeblocks.org/](http://www.codeblocks.org/)

Ara bé, com tot, per adoptar un nou entorn s'ha de tenir molta paciència, no es pot pretendre treballar igual que com ho feies amb l'entorn antic en dos dies. A l'entorn que estem acostumats trobem tot de seguida i no perdem temps, quan ens canviem sembla que ja no sabem res i les coses més senzilles ens costa trobar-les. Molta gent no té paciència per això. Per exemple no conec a ningú que estigui acostumat a fer servir Photoshop i es canviï a Gimp, perquè pot portar un bon temps adquirir la mateixa perícia amb un entorn nou.

---

### Post by Kette on 2011-11-21
Al mon GNU/Linux tens moltes opcions per fer programació. Tal com t'ha dit en wgarcia "Codeblocks"(Code::Blocks C++) esta molt bé, pot ser sigui el millor. També pots provar amb l'omnipresent "Eclipse" o amb "Netbeans" però de tots hi ha un que és clavat al Dev++, es diu Anjuta i és als dipòsits, de fet tots hi son.

---

### Post by Joan Marc on 2011-11-22
He estat trastejant el CodeBlocks i el Anjuta, i la veritat és que no he aconseguit que em compilin un programa amb C++ que sé del cert que funciona... Com be dius wgarcia, cada programa té el seu entorn i la seva manera de fer les coses, i ara mateix no tinc massa temps per posar-me a aprendre com funciona un altre programa.
Moltes gràcies de totes maneres, si algun dia tinc temps i ganes, provaré d'endinsar-me una mica més i intentar fer-los servir.

---

### Post by wgarcia on 2011-11-23
Suposo que també tindràs instal·lat el "build-essential", que és on estan tots paquets de desenvolupament, oi?

---

### Post by orestesmas on 2011-11-24
No veig gens clar aquest llistat: En una taula de particions del tipus MS-DOS només hi poden haver 4 particions primàries, numerades de 1 a 4. Si en tens més (com és el teu cas) una d'elles ha de ser "extended", però aquesta no conté dades, sinó que és com una mena de contenidor per ubicar-hi les altres particions, que sempre comencen pel número 5.

Aleshores tu no pots muntar la partició 3, sinó que has de muntar la 5, la 6, etc..

Ara bé, veig que totes les teves particions són de windows (NTFS) i només tens una /sda5 que és la swap. En resum: no tens cap partició on ubicar-hi el linux. Intueixo, per tant, que en reinstal·lar el windows 7 se te la va carregar i la va formatar en HPFS/NTFS.

Fixa-t'hi: la partició "extended (sda3)" abarca del cilindre 50645 al	59116, i la sda5 va del 58598 al	59116, o sigui que està continguda dins la sda3 (a la part final). I fixa't també que no hi ha cap partició que vagi a la part inicial de la extended (del cilindre 50645 al 58598), amb la qual cosa tens allí un espai lliure desaprofitat.

Després la partició sda4 comença just després de la sda3-sda5. En fi, un merder.

Jo si fos tu esborraria el disc sencer i ho tornaria a crear tot. Primer instal·la el windows i finalment el linux.

---

### Post by Joan Marc on 2011-11-24
> **wgarcia said:**
> Suposo que també tindràs instal·lat el "build-essential", que és on estan tots paquets de desenvolupament, oi?
Doncs no ho se, quan pugui ho mir-ho, gràcies.
> **orestesmas said:**
> No veig gens clar aquest llistat: En una taula de particions del tipus MS-DOS només hi poden haver 4 particions primàries, numerades de 1 a 4. Si en tens més (com és el teu cas) una d'elles ha de ser "extended", però aquesta no conté dades, sinó que és com una mena de contenidor per ubicar-hi les altres particions, que sempre comencen pel número 5.

Aleshores tu no pots muntar la partició 3, sinó que has de muntar la 5, la 6, etc..

Ara bé, veig que totes les teves particions són de windows (NTFS) i només tens una /sda5 que és la swap. En resum: no tens cap partició on ubicar-hi el linux. Intueixo, per tant, que en reinstal·lar el windows 7 se te la va carregar i la va formatar en HPFS/NTFS.

Fixa-t'hi: la partició "extended (sda3)" abarca del cilindre 50645 al	59116, i la sda5 va del 58598 al	59116, o sigui que està continguda dins la sda3 (a la part final). I fixa't també que no hi ha cap partició que vagi a la part inicial de la extended (del cilindre 50645 al 58598), amb la qual cosa tens allí un espai lliure desaprofitat.

Després la partició sda4 comença just després de la sda3-sda5. En fi, un merder.

Jo si fos tu esborraria el disc sencer i ho tornaria a crear tot. Primer instal·la el windows i finalment el linux.
Esborrar tot el disc? Uf, no se si m'atreviré... Si l'esborro tot, em carregaré la partició RECOVER que serveix per recuperar el W7 amb tots els paràmetres de fàbrica, i també la SYSTEM que aquesta no sé ni què és ni si es pot esborrar tant facilment... jo també trobo que hi tinc un merder i que seria la millor opció, pero no acabo de veure-ho clar.
Gràcies de totes maneres!

---

### Post by wgarcia on 2011-11-25
Una altra que et fan els de Microsoft. Et venen una llicència d'un sistema operatiu i no et donen un disc per reinstal·lar-lo si tens algun problema. Si peta el disc o es fa mal bé algun sector clau, has d'enviar l'ordinador al servei tècnic si vols tornar a tenir el sistema operatiu, tot i que tinguis còpia de seguretat de tot.

Penso de totes maneres que hi ha un procediment per crear-se un disc instal·lable a partir d'aquestes particions de recuperació, però jo no ho sé fer, en algun fòrum adequat potser es pot trobar informació de com fer-ho.

---

### Post by orestesmas on 2011-11-25
> **Joan Marc said:**
> 
Esborrar tot el disc? Uf, no se si m'atreviré... Si l'esborro tot, em carregaré la partició RECOVER que serveix per recuperar el W7 amb tots els paràmetres de fàbrica, i també la SYSTEM que aquesta no sé ni què és ni si es pot esborrar tant facilment... jo també trobo que hi tinc un merder i que seria la millor opció, pero no acabo de veure-ho clar.
Gràcies de totes maneres!

Bé, no cal esborrar tot el disc, de fet. Assumint que el windows i la seva partició de recuperació són les sda1 i sda2, jo només esborraria ls particions sda3, sda4 i sda5 i faria una instal·lació automàtica del linux a l'espai buit que m'hagi quedat.

Això si, assegura't que el windows és realment a les particions 1 i 2: arrenca en windows i explora una mica el disc amb aquella eina de gestió de discs que té: t'ajudarà a fer-te una composició de lloc.

---

### Post by Joan Marc on 2011-11-25
> **wgarcia said:**
> Una altra que et fan els de Microsoft. Et venen una llicència d'un sistema operatiu i no et donen un disc per reinstal·lar-lo si tens algun problema. Si peta el disc o es fa mal bé algun sector clau, has d'enviar l'ordinador al servei tècnic si vols tornar a tenir el sistema operatiu, tot i que tinguis còpia de seguretat de tot.

Penso de totes maneres crec que hi ha un procediment per crear-se un disc instal·lable a partir d'aquestes particions de recuperació, però jo no ho sé fer, en algun fòrum adequat potser es pot trobar informació de com fer-ho.

> **orestesmas said:**
> Bé, no cal esborrar tot el disc, de fet. Assumint que el windows i la seva partició de recuperació són les sda1 i sda2, jo només esborraria ls particions sda3, sda4 i sda5 i faria una instal·lació automàtica del linux a l'espai buit que m'hagi quedat.

Això si, assegura't que el windows és realment a les particions 1 i 2: arrenca en windows i explora una mica el disc amb aquella eina de gestió de discs que té: t'ajudarà a fer-te una composició de lloc.
Doncs aquesta pot ser una solució bastant més bona que l'altre...
Una pregunta: puc eliminar les particions directament entrant amb un LIVECD i quedar-me tant ample sense tenir cap problema, o he de seguir algun procediment per no carregar-m'ho tot?

PD: Si creieu que és convenient, obro un tema nou...

EDITO: Suposo que el procés serà el mateix que desinstal·lar l'Ubuntu definitivament, però en el meu cas, per tornar-lo a instal·lar de nou, i he trobat varis tutorials que diuen el mateix: Primer eliminar el GRUB i després les particions de l'Ubuntu des del Windows... Què us sembla?
[http://www.configurarequipos.com/doc1140.html](http://www.configurarequipos.com/doc1140.html)

---

### Post by orestesmas on 2011-11-27
> **Joan Marc said:**
> 
Una pregunta: puc eliminar les particions directament entrant amb un LIVECD i quedar-me tant ample sense tenir cap problema, o he de seguir algun procediment per no carregar-m'ho tot?


El que pots fer és arrencar una LIVE i dir-li que instal·li l'ubuntu, però a l'hora de particionar el disc, en lloc de dir-li que ho faci automàticament hauries d'escollir fer-ho "manual" i aleshores entraràs dins el partidor. Allí podràs esborrar les particions que no t'interessin fins a deixar espai buit.

Una vegada fet això pots fer dues coses:

1) Crees tu les particions linux manualment. Com a mínim hauries de crear-ne:
[LIST]
[*]Una per l'àrea d'intercanvi, d'una mida igual o lleugerament superior a la RAM que tingui el PC.
[*]Una pel sistems de fitxers arrel, formatada en ext4, i d'una mida mínima d'uns 10-30GB
[*]També és interessant crear-ne una tercera pel /home amb la resta de l'espai disponible, així pots tenir les dades en una partició independent, i eventualment pots reinstal·lar tot el sistema sense tocar per res les teves dades.
[/LIST]
2) Si tot l'anterior et resulta massa complicat, aleshores una vegada esborrades les particions que molesten tornes a arrencar amb la LIVE i li dius que usi l'espai lliure automàticament per instal·lar el linux.

---

