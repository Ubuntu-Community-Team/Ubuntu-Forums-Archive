---
title: "No puc actualitzar windows"
date: 2010-05-18
forum: Catalan Team
---

### Post by pserra on 2010-05-18
Hola,
aquesta lucyd m'està posant....
em va bé, però no em deixa accedir a la partició de windows com vaig comentar fa 2 semanes, al seu dia vaig fer updates del grub...i rés. sempre que vull accedir a la partició windows em surt la mateixa pantalla negra amb el guió blanc a intermitències a dalt a l'esquerra i no fa rés més.
He provat entrar amb el cd de recuperació, em comprova el sistema windows, em diu que està bé... però no arranca.
El cas es que he pensat instalar de nou el windows.... i necessita reiniciar per acabar la instalació... i quan reinicia.... em torna a sortir la "**ta pantalla negra" i no em deixa continiuar la instal·lació.
aquesta pantalla no em sortia mai fins que vaig passar-me a la Lucid, hi ha alguna manera de treure-la??
algú em pot ajudar?? El cas es que necessito treballar en software privatiu...

---

### Post by wgarcia on 2010-05-18
A l'enllaç que et vaig passar, i del qual vas posar el resultat d'aplicar el script ([http://ubuntuforums.org/attachment.php?attachmentid=156236&d=1273449054](http://ubuntuforums.org/attachment.php?attachmentid=156236&d=1273449054)), es veia que tens instal·lats múltiples grub i alguns d'ells a les particions de windows. No entenc perquè no has continuat a aquell fil en comptes d'obrir un altre. 

A més surt que tens fins i tot versions diferents de grub. 

Al mateix lloc posa com recuperar l'accés a aquestes particions:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by pserra on 2010-05-18
> **wgarcia said:**
> A l'enllaç que et vaig passar, i del qual vas posar el resultat d'aplicar el script ([http://ubuntuforums.org/attachment.php?attachmentid=156236&d=1273449054](http://ubuntuforums.org/attachment.php?attachmentid=156236&d=1273449054)), es veia que tens instal·lats múltiples grub i alguns d'ells a les particions de windows. No entenc perquè no has continuat a aquell fil en comptes d'obrir un altre. 

A més surt que tens fins i tot versions diferents de grub. 

Al mateix lloc posa com recuperar l'accés a aquestes particions:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Disculpa pel fil nou, avui repassaré l'enllaç al seu dia vaig veure el grub instalat a sda7 que es on tinc el linux...com que a posteriori l'he trastejat força ja no es així...
merci

---

### Post by pserra on 2010-05-18
> **pserra said:**
> Disculpa pel fil nou, avui repassaré l'enllaç al seu dia vaig veure el grub instalat a sda7 que es on tinc el linux...com que a posteriori l'he trastejat força ja no es així...
merci

Hola, wgarcia he seguit els consells de l'enllaç he fet els passos de l'enllaç, i m'he quedat igual...ja no se que més fer!!
Merci per l'interés... 
deu ser una tonteria.. però m'està posant...

---

### Post by wgarcia on 2010-05-18
Has utilitzat el programa "testdisk" i no t'ho ha solucionat?

---

### Post by pserra on 2010-05-18
> **wgarcia said:**
> Has utilitzat el programa "testdisk" i no t'ho ha solucionat?

Hola,
aquests darrers dies apart d'avui amb el testdisk,on he fet els passos OK, em sembla que ho he provat tot.. també vaig entrar des de el cd de recuperació del sistema (windows) i he polsat restaurar,i també  des de la consola windows he executat:
     bootrec/fixboot
     bootrec/fixmbr
i em penso que he tingut el windows bé... el grub.cfg apuntant al mateix lloc que sempre,però no se perquè se'm queda la pantalla negre i no arranca el punyetero windows!!
alguna altre suggerencia?
merci

---

### Post by pserra on 2010-05-18
No entenc, com es que fent un update em reconeix bé les particions... però no hi accedeix.....
Pot ser problema de grub?
es pot instalar el LILO? o es massa antic?

> pere@pere-portatil:~$ sudo fdisk -l
[sudo] password for pere: 

Disc /dev/sda: 320.1 GB, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9fca1fd5

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       13462   108133483+   7  HPFS/NTFS
/dev/sda2           13463       34639   170104252+   7  HPFS/NTFS
/dev/sda3           34640       37631    24033240    5  Estesa
/dev/sda4           37632       38913    10292224    7  HPFS/NTFS
/dev/sda5           34640       35199     4498168+   b  W95 FAT32
/dev/sda6           35200       35566     2947896   82  Intercanvi Linux / Solaris
/dev/sda7           35567       37631    16587081   83  Linux
pere@pere-portatil:~$ sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
pere@pere-portatil:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic

---

### Post by pserra on 2010-05-18
Algú em pot aconsellar de com puc accedir l'altre sistema operatiu?
No saps quina poca gracia em fa quan he reinstal·lat el grub, instal·lo part de l'altre sistema operatiu i quan vol reinciar per finalitzar l'instal·lació se'm queda amb la 'p**a' pantalla negra i el guió de dalt l'esquerra parpadejant....i no fa rés més!! he d'entrar amb el Super Grup per restaurar i entrar almenys a Ubuntu....
ni fet espressament...
porto  molta estona mirant amb el google... 
però sempre acabo al mateix lloc->pantalla negra per entrar a sda1
no entenc... des de que vaig instal·lar Lucid (que va lenta per engegar, però va bé)  em passa i no he avançat rés...
al grub.cfg les linies referents a sda1 son les mateixes que fa mesos:
           >    menuentry "Windows VISTA (loader) (on /dev/sda1)" {
              insmod ntfs
              set root='(hd0,1)'
              search --no-floppy --fs-uuid --set 1326bf044b43f4e8
              chainloader +1
                }
Merci

---

### Post by wgarcia on 2010-05-19
Però el script et continua mostrant que el grub està instal·lat en /dev/sda1 com es veia en els RESULT.txt que vas adjuntar?

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> Però el script et continua mostrant que el grub està instal·lat en /dev/sda1 com es veia en els RESULT.txt que vas adjuntar?
Hola wgarcia,
ho he tornat a fer segons enllaç passat, des de el live cd.....al peu de la lletra.
Explico la 'parrafada'  a veure si en treiem l'entrellat del que em passa, penso que anem pel bon camí.
He vist que ha canviat el arxiu adjunt.. passo enganxat el començament:


  > [SIZE="2"][SIZE="2"][SIZE="1"]              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 586850821 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 587047341 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 586949261 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 586998221 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr[/SIZE][/SIZE][/SIZE]
Ja no se si es normal però tinc el grub a moltes particions. Acabo de comprovar al petit acer que tinc, i no m'apareix a cap partició, només a la capçalera del .txt.
Després de fer l'operació al Testdisk  he fet segons el enllaç el sudo update-grub.He reiniciat i m'apareix la pantalla del grub antic, en un segon puc llegir"Load grub stage 1,5", després se'm  carreguen les opcions:
kernel1 bla,bla,bla...
kernel2 bla, bla, bla..
chainload into grub 2->si cliko->Error 11 Unrecogniced device string    press anyn key to continue...
Ubuntu 10.04LTS memtest+86

Que us sembla? com ho puc solventar? ja passo de fer 'esperiments pel meu compte'...merci.

---

### Post by wgarcia on 2010-05-19
No, no és normal, tens el grub legacy (el vell grub) que és el que t'arrenca el sistema al MBR del disc /dev/sda, però el grub 2 (el nou grub) a tot arreu.

El fet que el tinguis a /dev/sda1 és el que fa que no pugui arrencar el sistema privatiu que tens en aquesta partició. 

Has corregut "testdisk"? (sudo apt-get install testdisk)

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> No, no és normal, tens el grub legacy (el vell grub) que és el que t'arrenca el sistema al MBR del disc /dev/sda, però el grub 2 (el nou grub) a tot arreu.

El fet que el tinguis a /dev/sda1 és el que fa que no pugui arrencar el sistema privatiu que tens en aquesta partició. 

Has corregut "testdisk"? (sudo apt-get install testdisk)

si des de el live cd faig això em retorna:
```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
E: No s'ha pogut trobar el paquet testdis
```
ho he fet seguint el manual (descarregar/desempaquetar/executar)desde el live.
ara estixc al live i al fer sudo apt-get update i sudo apt-get upgrade
m'ha sortit el error de grub però no se com arreglar-ho i tinc por de 'liar-la' em pots ajudar?
primer em surt la finestra primera--no veig enlloc la linia que em parla!
li dono OK que es la unica 'opció'..
i em surt la pantalla segona de informació
i després la seguent que no he adjuntat que em mostra totes les particions i sembla que entre els claudators hauria de selccionar-ne una.. i el dubte es, com selecciono? he provat amb ratolí/teclat i rés... i quina partició hauria de seleccionar?
el pantallasso 3 es el que em mostra l'avis després de no seleccionar-ne cap.
Quins passos je de seguir?
Merci

---

### Post by wgarcia on 2010-05-19
Però encara pots accedir a ubuntu, oi?

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> Però encara pots accedir a ubuntu, oi?
si, a ubuntu des de que vaig instalar la lucid sempre he pogut entrar... ahir quan instalava el windos i em reiniciava el perdia, havia d-entrar amb el supergrub i restaurar...
com ho puc fer de fer 'net' de grub e instalar-ho correctament..

---

### Post by wgarcia on 2010-05-19
> **pserra said:**
> ahir quan instalava el windos i em reiniciava el perdia, havia d-entrar amb el supergrub i restaurar...

Això és lògic, perquè el windows et reescriu el MBR i esborra el grub. 

Intenta instal·lar i córrer el testdisk des de l'ubuntu que et funciona.

---

### Post by pserra on 2010-05-19
ahir ja hi vaig probar,
ja ho provare en 30 minuts,
lo de la connexio (altre fil) com ho puc reparar?
Merci

---

### Post by pserra on 2010-05-19
Ja hi he fet, a la partició de sda1 tinc un asterisc a l'esquerra..
he fet un update-grub.. he reiniciat però està tot igual...enlloc de carregar-se aquest grub, se'm carrega un altre on no em surt el windows7.

> TestDisk exited normally.
pere@pere-portatil:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda4
done
pere@pere-portatil:~$ 

---

### Post by wgarcia on 2010-05-19
Tinc dubtes amb quina versió de grub estàs començant, perquè si encara començes amb la versió 1 l'update-grub no fa res.

Al menú grub inicial que tens, què posa a la primera línia de títol?

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> Tinc dubtes amb quina versió de grub estàs començant, perquè si encara començes amb la versió 1 l'update-grub no fa res.

Al menú grub inicial que tens, què posa a la primera línia de títol?

em surt alguna cosa com loading stage1
si no toco rés entro a Ubuntu,
i si toco la tecla esc entro al grub sense títol, on tinc els 2 kernels amb els seus recorery mode, una linia on posa:
 chainload into  GRUB2 ->si cliko em surt ERROR  11  unrecognized device string
i al final el memtest...

NO SÉ, AIXÒ M'ESTÀ SUPERANT...no se si tornar a reinstalar el lucid o posar el koala... 
també voldria crear una partició per la /home i l'altre per l'arrel/
es molt difícil?

suposo que lo del grub potser s'arreglarà... 
i la connexió que m'ha petat també....
POTSER SERÀ LA SOLUCIÓ... son masses dies...QUE US SEMBLA??

---

### Post by wgarcia on 2010-05-19
Em sembla que el que passa és que tens el grub 2 però encara arrenca des d'un arxiu menu.lst. Per tant et passo unes instruccions a veure si almenys s'arregla el grub:

1.

Entra primer a l'ubuntu que et funciona i comprova que tens instal·lat "grub-pc"

i un cop comprovat reengega el sistema.

2. 

Un cop que et surt allò de Error 11 i després "Chainload into Grub 2" selecciona aquesta línia "Chainload..." i prem "e".

Veuràs una línia que comença amb "root" i després un ID de disc, del tipus:

root a4ca7983-f388-4b66-ab01-871a09e91660

Amb l'editor esborra "root" i posa "uuid", ara hauria de ser:

uuid a4ca7983-f388-4b66-ab01-871a09e91660

Quan acabis pressiona "b" per engegar el sistema.


3. 

Ara hauries de veure el menú del grub, amb una primera línia de títol que diu Grub 1.97 (o 1.9"8") i algunes coses més. 

Escull el nucli que vols arrencar i prem intro per començar el sistema.

4.

Un cop que estiguis a l'escriptori, obre una línia de comandes i corre la següent instrucció:

sudo upgrade-from-grub-legacy

A veure si això ho arregla.

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> Em sembla que el que passa és que tens el grub 2 però encara arrenca des d'un arxiu menu.lst. Per tant et passo unes instruccions a veure si almenys s'arregla el grub:

1.

Entra primer a l'ubuntu que et funciona i comprova que tens instal·lat "grub-pc"

i un cop comprovat reengega el sistema.

2. 

Un cop que et surt allò de Error 11 i després "Chainload into Grub 2" selecciona aquesta línia "Chainload..." i prem "e".

Veuràs una línia que comença amb "root" i després un ID de disc, del tipus:

root a4ca7983-f388-4b66-ab01-871a09e91660

Amb l'editor esborra "root" i posa "uuid", ara hauria de ser:

uuid a4ca7983-f388-4b66-ab01-871a09e91660

Quan acabis pressiona "b" per engegar el sistema.


3. 

Ara hauries de veure el menú del grub, amb una primera línia de títol que diu Grub 1.97 (o 1.9"8") i algunes coses més. 

Escull el nucli que vols arrencar i prem intro per començar el sistema.

4.

Un cop que estiguis a l'escriptori, obre una línia de comandes i corre la següent instrucció:

sudo upgrade-from-grub-legacy

A veure si això ho arregla.
Ok, al editar el grub m'ha carregat el grub2 (versio 1.98).. la particio windows no fa rés...
entro a ubuntu i el pc-grub si que el tin instal·lat i si faig el:
sudo upgrade-from-grub-legacy
m'obre la finstra que se'm obria des de el live(adjunta) dubtes:
-per no 'liar-lo més' quina partició escullu i com? amb el ratolí no fa rés i el teclat he provat sense canvis...
Merci

---

### Post by wgarcia on 2010-05-19
Escull /dev/sda, has de prèmer la barra d'espai per escollir l'opció, no continuïs sense escollir cap "device" perquè sinó et donarà Error 15 en començar el sistema.

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> Escull /dev/sda, has de prèmer la barra d'espai per escollir l'opció, no continuïs sense escollir cap "device" perquè sinó et donarà Error 15 en començar el sistema.

Gràcies wgarcia,
només he escollit la primera opció /dev/sda,
i se'm ha executat correctament:

> [SIZE="1"]pere@pere-portatil:~$ sudo upgrade-from-grub-legacy
[sudo] password for pere: 
0
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda4
done

GRUB Legacy has been removed, but its configuration files have been preserved,
since this script cannot determine if they contain valuable information.  If
you would like to remove the configuration files as well, use the following
command:

  rm -f /boot/grub/menu.lst*

pere@pere-portatil:~$ [/SIZE]
he reiniciat, 
ara ja em surt el grub "versió 1.98 1ubuntu6"
amb totes les particions, però he provat seleccionar la sd1 i la sd4(windows) i em torna a apareixer la meva estimada pantalla negra...I NO FA RÉS... no carrega rés.
adjunto el

---

### Post by wgarcia on 2010-05-19
Bé, jo aquí no et puc ajudar més, perquè el problema amb les teves particions amb sistema privatiu és que s'ha posat grub en elles sobreescrivint els arxius d'arrencada de windows. Hauries de reinstal·lar l'arrencada d'aquestes particions, però jo no se com fer-ho en windows, i a més segurament t'afectarà el MBR del disc i hauras de tornar a instal·lar el grub 2 (cosa que es pot fer de totes maneres sense problemes). 

L'enllaç que et vaig passar explicava un parell de maneres de recuperar l'arrencada de windows. També podries provar a córrer un altre cop el "testdisk".

---

### Post by pserra on 2010-05-19
> **wgarcia said:**
> Bé, jo aquí no et puc ajudar més, perquè el problema amb les teves particions amb sistema privatiu és que s'ha posat grub en elles sobreescrivint els arxius d'arrencada de windows. Hauries de reinstal·lar l'arrencada d'aquestes particions, però jo no se com fer-ho en windows, i a més segurament t'afectarà el MBR del disc i hauras de tornar a instal·lar el grub 2 (cosa que es pot fer de totes maneres sense problemes). 

L'enllaç que et vaig passar explicava un parell de maneres de recuperar l'arrencada de windows. També podries provar a córrer un altre cop el "testdisk".
Merci, wgarcia he aprés molt amb el grub, aquesta nit reinstal·laré el Lucid e intentaré acabar la instalació del windows a veure si m'ensurto. Es una llàstima que no ens haguem sortit...
Merci per tot, a veure si ja m'ensurto...

---

### Post by pserra on 2010-05-20
després de perdre moltes estones, al final he formatejat les particions de ubuntu i windos, De dividid la partició de ubuntu per/ i la /home i l'he intalat i tot perfecte, em reconeix els 2 sistemes, m'engega més ràpit. TOT OK.
em sembla que hi tenia masses pedaços...

---

