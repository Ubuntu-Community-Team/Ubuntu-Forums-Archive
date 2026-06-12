---
title: "Ha deixat de reconèixer-me la memòria externa"
date: 2010-10-25
forum: Catalan Team
---

### Post by Martima on 2010-10-25
Hola a tothom i auxili a qui pugui ajudar-me.

Segurament és una parida, però si no ho saps, estàs perdut.

Vaig comprar una memòria externa USB de 500Gb. Model... a la caixa hi diu "WD elements SE".

Volia fer una còpia de seguretat perquè l'ordinador ja estava a petar. He anat gravant-hi un munt de coses i encara que mooooooolt a poc a poc, se'm va anar gravant bé.

Però estic a mitja còpia (ho he anat fent per carpetes perquè si feia una còpia de tot alhora, quedava penjat i no copiava bé).

Total, que suposo que deuria sortir de l'ordinador quan la memòria externa estava "pensant" (?) i quan hi he volgut tornar a entrar sembla que no me la reconeix.

Em diu el següent missatge:


[http://img220.imageshack.us/img220/5563/capturair.png](http://img220.imageshack.us/img220/5563/capturair.png)


Algú sap com ho puc fer perquè m'ho detecti i pugui continuar amb la còpia de seguretat, siusplau?

Com que és una còpia de seguretat, preferiria no haver de formatejar la unitat, lògicament.

Molt agraït.

Martí.

---

### Post by kukat on 2010-10-26
Hola!!

Doncs el que tens que fer t'ho diu la captura que ens has passat:

"El sistema de fitxers NTFS està inconsistent o té un error de maquinari......"
"En aquest cas executa CHKDSK /F a windows"
"Després reinicia a Windows una altra volta"
"No oblides el paràmetre /F, és molt important" 

;)  

Pots veure la documentació de la comanda CHKDSK [a la web de Windows]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true").

---

### Post by Martima on 2010-10-26
Ah. És que tot això em sona una mica a xinès. A veure si me'n surto.

Avui he connectat la memòria a un ordinador amb windows i funcionava perfectament sense fer res de res. Em pensava que havent desconectat la memòria amb "sortir de forma segura" després de tenir-lo conectat amb el windows, ja em funcionaria a casa amb l'Ubuntu. Però ara l'he conectat aquí i veig que continua igual.

Mi goso en un poso.

Miraré de fer el checkdsk /f aquest des d'un ordinador amb windows. Espero m'acabi funcionant.

Quines coses, la informàtica.


Gràcies, eixerits!

---

### Post by kimet on 2010-10-26
Mira si et reconeix el dispositiu:
```
lsusb
```
```
sudo fdisk -l
```

Em sembla que per fer funcionar el driver ntfs-3g fa falta fuse 8 no ho se segur)
```
lsmod | grep fuse
```

A veure si en pots aclarir alguna cosa.

---

### Post by Martima on 2010-10-26
Ein?? que sóc un passerell, jo!

Si us ha de servir d'alguna cosa per entendre què passa, diré que quan el conecto em surt el missatge que us adjuntava al primer correu, però que si faig "Llocs" sí que m'apareix identificada la memòria USB aquesta. Al menú desplegable m'hi apareix "ordinador" "unitats de disquet" i "elements". Aquest últim és la memòria USB de 500Gb en qüestió.

Intento escriure el que em dius, a veure si em sabeu traduïr el que em surti. Procedeixo:

_**lsusb**_

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:0805 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 1058:1023 Western Digital Technologies, Inc. 
Bus 001 Device 008: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


_**SUDO FDISK -L**_

Disc /dev/sda: 40.0 GB, 40020664320 octets
255 heads, 63 sectors/track, 4865 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb776b776

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Estesa
/dev/sda5            4773        4865      746991   82  Intercanvi Linux / Solaris

Disc /dev/sdf: 500.1 GB, 500105740288 octets
255 heads, 63 sectors/track, 60801 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e78d

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdf1               1       60802   488383488    7  HPFS/NTFS


_**LSMOD | GREP FUSE**_
No fa res. Em torna a sortir la primera línia com si esperés una nova línia.

---

### Post by kimet on 2010-10-26
El dispositiu te'l reconeix, prova muntar-lo.
```
mount /dev/sdf
```
Si no et deixa, pova-ho com a root,(amb sudo al devant)

---

### Post by Martima on 2010-10-26
Vaig provar de montar-lo des de "sistema" --> "administració" --> "utilitats de discs" --> "dipositius perifèrics" --> "Disc dur de 500Gb" --> "munta el volum"  Alternativament, també "treu de forma segura". Però em surt el missatge que vaig adjuntar-vos al primer correu.

És curiós perquè em va estar funcionant durant uns quants dies amb aquest ordinador, on només hi tinc ubuntu. Però va deixar de fer-ho. Aquest matí he vist que en un ordinador amb windows em fa perfecte. Veig els arxius que hi he gravat. Els puc copiar, etc...

Intento el que em dius:

_**mount /dev/sdf**_

mount: no s'ha pogut trobar /dev/sdf a /etc/fstab o /etc/mtab


_**sudo mount /dev/sdf**_

mount: no s'ha pogut trobar /dev/sdf a /etc/fstab o /etc/mtab


Hummm....

---

### Post by kimet on 2010-10-26
prova:
```
mount /dev/sdf /media/sdf
```

Si no existeix /media/sdf el crees o els muntes en un altre lloc.
```
sudo mkdir /media/sdf
```
Si funciona haurás d'editar /etc/fstab perque te'l munti automaticament.

---

### Post by Martima on 2010-10-26
Nano, no hi entenc massa, però em penso que ja ho tens encarrilat. Què li escric amb això dels fitxers??


marta@nanosdesants:~$ mount /dev/sdf /media/sdf
mount: només l'usuari root pot fer això
marta@nanosdesants:~$ sudo mount /dev/sdf /media/sdf
[sudo] password for marta: 
mount: el punt de muntatge /media/sdf no existeix
marta@nanosdesants:~$ sudo mkdir /media/sdf
marta@nanosdesants:~$ sudo mount /dev/sdf /media/sdf
mount: haureu d'especificar el tipus del sistema de fitxers
marta@nanosdesants:~$

---

### Post by kimet on 2010-10-27
al fitxer /etc/fstab, amb un editor de text, jo faig servir nano.
```
sudo nano  /etc/fstab
``` 
al final hi enganxes la linia:
```
/dev/sdf /media/sdf ntfs-3g defaults        0           0
```
guardes els canvis ctrl+o (tecla control i lletra "o" a l'hora) i surts ctrl+x.
muntes tot:
 ```
sudo mount -a
```
tindies muntat el dispositiu a /media/sdf
-Si tot i així no te'l munta torna a windows i torna  a executar la comanda que t'ha dit en kukat anteriorment i tenca la sessió correctament.
-revisa si tens instal.lat ntfs-3g
-mira si esta carregat el mòdul fuse 
```
lsmod | grep fuse
```
si no els carregues
 ```
sudo modprobe fuse
```

i ja no se m'acudeix res mes

bon profit.

---

### Post by kukat on 2010-10-27
Val, però en la línia

***sudo nano /etc/fstab***

que ha dit en kimet, recorda que pots utilitzar altres editors de text. El més senzill és "gedit"

***sudo gedit /etc/fstab***

;)

---

### Post by Martima on 2010-10-27
PROGRESSOS!!

Ahir conectar la memòria externa a un ordinador amb windows, vaig veure que allà funcionava perfectament (aparentment) i pensant que ja havia quedat solucionat, vaig venir a casa, però no s'havia arreglat, continuava igual.

Avui l'he tornat a conectar a l'ordinador amb windows, però tal i com deia en Kukat en el seu primer missatge, he fet un chkdsk i he reiniciat i mira per on, que com a mínim, ara a casa ja torno a veure la memòria externa i torna a funcionar. Perfectament? no! sembla que hi ha hagut alguna cosa perduda entremig. Poso dades:

Ara que ja se m'identifica la memòria, clico i desplego "SISTEMA" --> "Administració" --> "Utilitats de disc". Selecciono el USB de 500Gb i clico botonet "Comprova sistema de fitxers" per veure si tot va bé.

Em diu:
A. S'ha produït un error mentre es realitzava l'operació "elements" (partició 1a WD elements 1023): el dispositiu està ocupat.
B. A detalls: Device is mounted and online capability in fsck tool for file systems.

Com que no tinc clar si això vol dir que hi ha un problema o no, dins de la mateixa finestra, clico sobre "Estat de l'SMART"   al costat d'aquest botó m'hi surt un avís "El disc conté alguns sectors erronis".

Dades de l'SMART: Cicles d'energia: 38
                                 1 sector malmès.

Em surt el següent:

[http://img3.imageshack.us/img3/9693/capturaox.jpg](http://img3.imageshack.us/img3/9693/capturaox.jpg)


Alguna recomanació per reparar aquest "sector malmès"???? és greu? em pot donar més problemes per a prosseguir amb la meva còpia de seguretat? Cal que m'hi preocupi? és una parida??

Moltes gràcies a l'interès prestat per tots plegats i si algú em pot arrodonir amb una última resposta a aquest problema secundari, encara molt més agraÏt.

Martí.

---

### Post by Martima on 2010-11-03
Bé, tornem-hi. Segona part. He "resolt" el problema anterior, però en tinc un de nou (o el mateix amb diferent expressió).

Al final, vaig conectar la memòria USB a un ordinador que tenia windows. Allà sempre m'ha permès visualitzar la memòria USB. Després d'intentar chkdsk /F sense poder finalitzar la comprovació, he optat per salvar al windows el que he pogut de la memòria USB (quasi tot) i formatejar la memòria.

Hi havia alguns arxius danyats, els quals m'apareixien com si pesessin 0Mb.

Després de formatejar la memòria, he comprovat altra vegada el chkdsk /F i finalment m'ha dit que el disc era correcte. Visca!! ja tenia la memòria buida i em donava correcta la comprovació chkdsk /F.

Avui he retornat a l'ordinador amb UBUNTU, a veure si per fi podia copiar la resta de còpia de seguretat pendent.

Però l'alegria no ha durat gaire.

He aconseguit que l'Ubuntu em reconeix la memòria en qüestió. Però em diu que "El disc conté alguns sectors erronis". Em diu també que hi ha 2 sectors malmesos i em parla d'un error en un re-mapeig que no sé què és però sembla que l'origen de tot plegat està allà. Tot això ja m'ho deia abans de formatejar-lo des de l'ordinador amb windows. Sembla que he arreglat un problema (com a mínim, ara veig la unitat des de l'ordinador amb ubuntu), però l'origen de tot és com si continués igual.

I segueixo sense poder fer la còpia de seguretat sense que se'm facin malbé alguns arxius. Ara com ara tinc la memòria USB buida, o sigui que estic disposat a fer-li "marranades" si convé per tal d'arreglar el tema sense por a perdre res.

[http://img695.imageshack.us/img695/214/capturacoi.png](http://img695.imageshack.us/img695/214/capturacoi.png)

[http://img200.imageshack.us/img200/9800/captura1h.png](http://img200.imageshack.us/img200/9800/captura1h.png)

[http://img155.imageshack.us/img155/2159/captura2r.png](http://img155.imageshack.us/img155/2159/captura2r.png)

---

### Post by kukat on 2010-11-04
Jo el que faig quan hi ha dos sectors defectuosos és passar-li el HDD Regenerator. 

El pots trobar a qualsevol LIVE CD de Hiren's Boot:
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Ara, jo donaria el disc dur per mig-mort. M'explique: El HDD Regenerator pot arreglar els sectors (sí, _físicament_!!), però probablement, dins d'un any, o pot ser dins d'any i mig, o "*ves a saber quan*", podria tornar a les mateixes....bé, igual no passa mai,  però **jo ja no el consideraria un disc dur segur per a fer còpies de seguretat**...... no se si m'explique. ..

Salut!

EDITO: Per cert, el disc dur ha tingut algun colp, o ha pogut fer-se malbé d'alguna forma????

---

### Post by kukat on 2010-11-04
Ostres, han llevat el HDD Regenerator, i l'han substituit per una alternativa gratuïtat: 

[http://www.hdat2.com/download.html](http://www.hdat2.com/download.html)


Així que ara és més fàcil. Ho pots baixar amb el Live CD d'abans, o de la seua web oficial com a ".exe"....no hi ha versió per a Linux.

---

### Post by Martima on 2010-11-04
Pues vaya!
 
No, no li he donat cap cop. El vaig comprar de nou en nou per a la còpia en qüestió.
 
Sóc molt cuidadós amb les coses i l'he tractat com caldria esperar d'un material informàtic.
 
Només es pot haver fet malbé gravant. Ja de nou en nou anava molt lent. Però si t'hi fixes, a la captura de pantalla que ajduntava a la 1a part de la meva consulta, diu que hi ha 1 sector erroni. No obstant, ara m'indica que hi ha 2 sectors erronis.
 
Anem de mal en pitjor.
 
Doncs sí que m'ha servit la memòria aquesta, tu!
 
Algun dia d'aquests provaré el programa que em dius, a veure què tal. Gràcies.
 
Snif, snif.
 
Podria ser que el problema vingués pel fet que la memòria venia preparada per windows (a la capsa no indica altra cosa) i a l'haver conectada amb ubuntu hagi petat alguna cosa?? sembla que d'inici el disc dur duia un executable perquè tot funcionés bé (amb windows) i aquí la cosa ja deuria fallar. Podria ser una cosa d'aquest estil??
 
Joé, que fa dues setmanes em va costar 80euros el trasto. Cagum l'ou!

---

### Post by PatrickVogeli on 2010-11-04
garantia? Un disc dur que dura molt poc o ve trencat de fàbrica no es del tot infreqüent... 

Obviament, no té res a veure ni amb windows ni amb linux ni res semblant amb aixo. Simplement aquest disc dur ha durat poc, a vegades passa. Si no va bé, que te'l passin en garantia i a funcionar.

Salut

---

### Post by kukat on 2010-11-05
Jo de tu li passaria el HDD Regenerator o aquest altre que t'he passat (aquest últim encara no l'he provat).


Si et troba algun sector erroni **déus de tornar-lo a la tenda amb la garantia** i comentar-los quin és el problema. Jo de tu no comentaria res de GNU/Linux. Ja em veig al "listillo" de la tenda asseguran-te que "pot ser" siga un problema amb GNU/Linux per a no canviar-te'l.
Que hi ha de molt llests a les tendes...
XD

---

