---
title: "WIFI no funcion amb Jaunty"
date: 2009-04-24
forum: Catalan Team
---

### Post by venusfenix on 2009-04-24
Buenas,

tinc un laptop Acer 7520 AMD 64x2 i ara amb JAUNTY

he sigut uns dels primers en actualitzar-me a jaunty.

he tingut algun problema amb la nvidia, pero ja conegut, el tema ha sigut que amb l'actualizatcio del Jaunty, m'ha possat tot el soft a l'ultima i temes com la nvidia i wifi, doncs no funcionaba amb el hardy i com era d'esperar, amb el jaunty tampoc.

He tirat enderrere el tema nvidia i tot be. el probleme el tinc amb el tema wifi.

he desinstal.lat el wicd 1.5.9. per posar-me el 1.5.5. doncs aquest si que em funciona, ara, tampoc.
Es possible que tingui que tornar a instalar un driver per activar la wifi??

un apunt mes, per cable no hi ha cap probleme, pero no veig cap icona com sempre passaba al hardy heron, que estaba executant de fons.
ara, vaig a l'opcio internet, executar wicd i no passa res.
no apareix cap finestra ni res.

---

### Post by socderafel on 2009-04-24
quin model de targeta wifi tens?

---

### Post by venusfenix on 2009-04-24
et paso la resposta del sistema a l'ordre "lspci"


00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


adicionalment, tinc el ndriswrapper instal.lat amb el net5211, em surt un missatge de "unable if hardware is present" pero un cop entrant a ndiswrapper en surt que el driver esta instal.lat y hardware present.

---

### Post by socderafel on 2009-04-24
crec que les atheros estaven donant algun problema.en trovar info te la passe.
Tinc entés que els drivers que porta ubuntu per a l'atheros no funcionen...

prova aço:

[http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)

---

### Post by PatrickVogeli on 2009-04-24
El wicd esta als repositoris del Jaunty! Esborra la versio que tinguis, si has posat el wicd al sources.list esborra'l i fes un sudo apt-get update i per ultim instal·la la versio que hi ha als repositoris d'ubuntu.

Aixo que comentes tambe em va passar: a l'instal·lar una versio baixad directament de la web del wicd, a l'executar wicd-client em donava no se quin error. Despres vaig veure que el wicd esta als repositoris, aixi que el vaig esborrar i el vaig instal·lar des dels repos i ale, a funcionar!

EDITO: has oberts dos temes amb la mateixa pregunta al mateix forum, mal fet!

---

### Post by venusfenix on 2009-04-25
buenas,

moltes gracies, ho probaré, el suport que doneu no sabeu lo be que va.

no he obert 2 temes, simplement he explicat l'escenari, els problemes que ha surtit i que he resolt per mi mateix, i el probleme que encara queda, que es el motiu d'aquest post.

intento probar-lo ara mateix i donar-vos una resposta.

moltes gracies.

---

### Post by venusfenix on 2009-04-25
acabo de probaro, i ara funciona.

l'ultima versio del wicd em funciona, quan normalment amb el 1.5.5 ja era suficient.
la finestra s'obre i tot, pero nomes tinc la xarxa per cable, no tinc wireless.

es posible que tingui que fer el que diu socderafel.

enga, us mantic informats!!

gracies,

---

### Post by venusfenix on 2009-04-25
buenas,

ultim informe, encara no funciona, el wicd el faig funciona i "rula" pero nomes veig la conexio per cable.
ara mateix, el ndiswrapper diu que el net5211.inf  que ja tenia instal.lat i que funcionava, ara diu que el hardware no es present.

en linea de lo que diu socderafel, en l'opcio administracio|controladors de maquinari, en diu que puc utilitzar el ath5 de madwifi que funciona amb la mayoria de atheros, pero al activar-lo diu que queda deshabilitat... etc... amb la cual cosa, em quedo com estaba.

espero noticias!!!!!

gracies,

---

### Post by venusfenix on 2009-04-25
he recuperat el fil on vaig exposar per primer cop aquest probleme i he intentat repetir lo que en el seu moment en vam indicar.

el tema es que ara no funciona, sembla que tot gira a traves d'un directori de acer i que ara no tinc.

recordo que el problem inicialment, es que el meu portatil te wifi, pero es conecta per botons externs i amb ubuntu queden inhabilitats.

potser que torni a tenir el mateix probleme???

gracies,

---

### Post by venusfenix on 2009-04-25
he llegit en forums ubuntu nort-americanes, que diuen que els drivers de Atheros que venen amb el jaunty no son correctes, i s'ha de desinstal.lar i descarregar uns altres, ho he fet, pero tampoc funciona, 

necesito ubuntu-ajuda!!!

gracies,

---

### Post by venusfenix on 2009-04-26
he probat de fer el que comentaba socderafel i en un pas, el comentari que diu el link es que no ha de tornar cap missatge, en el meu cas dona el següent:

sudo modprobe ath_pci


WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


??? llavors???

tambe he probat de fer el que he trobat en:
[http://ubuntuforums.org/showthread.php?p=7141577#post7141577](http://ubuntuforums.org/showthread.php?p=7141577#post7141577)

pero tampoc.

es una pena, doncs tenir portatil perque no disfrutar de la mobilitat.... jo...

agrairia qualsevol ajuda o idea.

gracies,

---

### Post by venusfenix on 2009-04-26
he fet un sudo ifconfig


eth0      Link encap:Ethernet  HWaddr 00:1b:38:68:9e:c4  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe68:9ec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:485124 (485.1 KB)  TX bytes:89115 (89.1 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4580 (4.5 KB)  TX bytes:4580 (4.5 KB)

---

### Post by PatrickVogeli on 2009-04-26
els erros que comentes al principi no son errors, sino warnings. Es solucionen posant .conf com a extensió fitxer que has creat a /etc/modprobe.d

De totes maneres, si no t'ha funcionat, encara possant-hi el .conf al final tampoc et funcionara.

salut

---

### Post by PatrickVogeli on 2009-04-26
no he dit res xD

---

### Post by papapep on 2009-04-26
Jo tinc el mateix xip a un Acer Aspire One, i només m'ha calgut posar a /etc/modprobe.d/blacklist.conf la línia:

```
blacklist acer_wmi
```

Això sí, aquest cas em funciona directament, i molt i molt bé, amb el Network Manager (primer cop...).
Amb el mòdul ath5k de la Jaunty ja m'ha funcionat correctament, no m'ha calgut ni activar el Madwifi alternatiu per a Atheros de Sistema > Administració > Controladors de maquinari.

Seria interessant veure quins mòduls tens carregats (i saber quin portàtil tens en concret):

```
lsmod
```

Per cert, ho has provat amb el Network Manager, abans d'instal·lar el Wicd?

---

### Post by venusfenix on 2009-04-26
buenas

papapep, 

potser, que ja he probat tantes coses.... ??? que esta tot una mica liat.

os paso el resultat de lsmod:


Module                  Size  Used by
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
wlan_scan_sta          22912  0 
ath_rate_sample        22400  1 
ath_pci               224960  0 
wlan                  258848  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               339088  3 ath_rate_sample,ath_pci
ndiswrapper           250624  0 
joydev                 20864  0 
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_seq_dummy          11524  0 
snd_hda_intel         557364  2 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               69512  0 
compat_ioctl32         18304  1 uvcvideo
snd                    78792  13 snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                64028  0 
soundcore              16800  1 snd
k8temp                 13440  0 
pcspkr                 11136  0 
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
serio_raw              14468  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
nvidia               8106480  36 
usbhid                 47040  0 
forcedeth              68368  0 
ohci1394               42036  0 
ieee1394              108288  2 sbp2,ohci1394
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit


en quant al portatil, es un acer 7520 AMD turion 64x2

necesites mes info??

gracies,

---

### Post by venusfenix on 2009-04-26
he probat d'afegir el que comentes, i he reiniciat maquina i res.
el wicd em diu que no troba cap xarxa wifi.

es millor si probo que desfer i tornar al network manager??

gracies

---

### Post by papapep on 2009-04-26
> es millor si probo que desfer i tornar al network manager??


Crec que et cal començar de nou. O sigui que sí, desinstal·la el Wicd i posa el Network Manager.
Quan ho hagis fet (**i reiniciat l'ordinador**), torna a enganxar el resultat de:

```
lsmod
```

i de:

```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by PatrickVogeli on 2009-04-26
No he dit res xD

---

### Post by venusfenix on 2009-04-26
buenas, Papapep,

sembla que comença a funcionar!!
inclus el led s'encen.

et paso el resultat de lsmod:


Module                  Size  Used by
wlan_wep               14592  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
wlan_scan_sta          22912  1 
ath_rate_sample        22400  1 
ath_pci               224960  0 
wlan                  258848  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               339088  3 ath_rate_sample,ath_pci
joydev                 20864  0 
ndiswrapper           250624  0 
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  2 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_pcm_oss            52352  0 
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
uvcvideo               69512  0 
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              34064  2 snd_seq,snd_pcm
psmouse                64028  0 
sdhci_pci              16896  0 
k8temp                 13440  0 
compat_ioctl32         18304  1 uvcvideo
pcspkr                 11136  0 
snd                    78792  13 snd_hda_intel,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
nvidia               8106480  36 
serio_raw              14468  0 
sdhci                  27396  1 sdhci_pci
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
forcedeth              68368  0 
ohci1394               42036  0 
ieee1394              108288  2 sbp2,ohci1394
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit


i de cat /etc/modprobe.d/blacklist.conf

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi


ara probo de fer la conexio, encara m'estic barallant, pero scaneja la xarxa, etc...

---

### Post by venusfenix on 2009-04-26
mes dades, el network manager em dona un llistat de les xarxes disponibles, i me he conectat, no ha casa, per error, a un altre xarxa.
misteriosament, no em surt la meva, i malgrat que l'he configurat, intenta conectar-se i res.... ??

suposo que ara, el tema es insistir fins que funcioni.

per altre banda, quan em conecto per cable, malgrat funciona, l'icona no camvia, i diu que no pot gestionar xarxes per cable (?) pero funciona...

alguna aportacio??

gracies,

---

### Post by venusfenix on 2009-04-26
buenas,

continuo tenin problemes, la xarxa no em surt al llistat, fa l'intentona de conectar-se pero res, durant uns pocs segons es conecta (durant la validacio) pero despres es desconecta.
quant el llistat mostra la xarxa, la senyal es molt fluixa, i tinc el router al costat del portatil, aixo, el confirmo amb un screenlet, que diu que rep el 5% de la senyal. quan lo normal es rebre'l al 100%.

ajuda!!!

gracies,

---

### Post by socderafel on 2009-04-27
has provat l'opció de connectar a una xarxa oculta,o  connectar a un altra xarxa o xarxa nova? hi has de posar totes les dades a ma. Quan estava jo a kubuntu i el knetwrkmanager, així em funcionava...

---

### Post by venusfenix on 2009-04-27
ho he probat pero res, pero em pregunta un munt d'histories,
hi ha cap web que t'expliqui com funciona?
pregunta el ssid, el bssid, la adreça mac, etc...
jo nomes he posar el ssid, la clau wep i tirando. pero res.
em resulta una mica extrany que no surti la meva xarxa a la llista, i quan comença la validació de xarxa, abans d'abandonar-la, la senyal esta al 5% i no al 100%, i aixo també m'estrany, i mes si estás a un pam del router. 

igualment, em mirare ve totes les opcions del networking manager, no sigui que hi hagi alguna historia que no estigui contemplant ara mateix.

gracies,

---

### Post by venusfenix on 2009-04-27
RES DE RES,

ohhhh, aixo no acaba de funciona!!!!

no hi ha cap manera??

gracias,

---

### Post by socderafel on 2009-04-27
la veritat es que no es normal que sols et done un 5% estant a un pam dem router... 
Anim que a la fi ho conseguirem . Vaig a buscar-te un poc d'info per ahi...

---

### Post by venusfenix on 2009-04-28
moltes gracies, espero les teves notes/info.

una anomalia, "por así decirlo", de la wifi, es que al final s'acaba conectant a cualsevol xarxa, encara que estigui proteguida, en surt conectada, i es crea el perfil i tot.

us diu res???

gracies,

---

### Post by ilku on 2009-04-28
Hola company:
Jo de tu, treuria la clau wep, per descartar un problema de validació. T'ho dic perquè, jo se d'un router que no em deixa conectar-me amb encriptació wep amb l'ubuntu, ni amb XP, pero si amb vista. Això nomes em passa amb aquest router en concret, amb altres si que puc amb qualsevol tipus d'encriptació.

---

### Post by papapep on 2009-04-28
> una anomalia, "por así decirlo", de la wifi, es que al final s'acaba conectant a cualsevol xarxa, encara que estigui proteguida, en surt conectada, i es crea el perfil i tot.


Però en fer aquesta connexió que dius, pots navegar?? o no??

A banda del que et diu l'Ilku, que pot ajudar-te, jo provaria a instal·lar el controlador propietari que et surt a Sistema > Administració > Controladors de maquinari, a veure què fa.
Millor que provis primer una cosa i després l'altra, sinó, si hi ha canvis, no sabràs què els ha causat.

---

### Post by socderafel on 2009-04-28
> **ilku said:**
> Hola company:
Jo de tu, treuria la clau wep, per descartar un problema de validació. T'ho dic perquè, jo se d'un router que no em deixa conectar-me amb encriptació wep amb l'ubuntu, ni amb XP, pero si amb vista. Això nomes em passa amb aquest router en concret, amb altres si que puc amb qualsevol tipus d'encriptació.

no havia pensat jo en això, i mira que em va passar fa res amb kubuntu i el knetworkmanager. prova a canviar al router el tipus de clau de WEP a WPA, a veure si així et deixa...

---

### Post by roquet on 2009-04-28
has provat d'anar a sistema - administració - controladors de maquinari i mira que no siguin controladors restringits?

---

### Post by venusfenix on 2009-04-28
buenas, i sobre tot, moltes gracies,

abans de provar de treure la clau WEP, com que venia amb el router d'ONO, he preferit fer la resta de les vostres opcions,

i quan vaig a sistema>administracio>controladors de maquinari, diu que estic usant un alternatiu madwifi del atheros:

"Controlador alternatiu «madwifi» per a les targetes LAN sense fil Atheros

Activeu aquest controlador només si teniu problemes amb la vostra connexió LAN sense fil.

Avui dia el controlador lliure «ath5» hauria de funcionar amb la majoria de les targetes Atheros, tot i que pot ser que en alguns ordinadors aquest controlador alternatiu (però de propietat) funcioni més bé o bé sigui l'únic que funcioni."


i si vaig activa'l, llavors em marca com deshabilitat.

no hi ha manera de fer-lo instal.lar??

gracies,

PD: continuaré informa'm

---

### Post by PatrickVogeli on 2009-04-28
mmm a veure.. seria interessant que desfessis absolutament tot el que has fet (afegir linies al blacklist, etc etc), reinciis l'ordinador i ens diguis que pots fer ara i que obtens al fer un lsmod.

salut!

---

### Post by venusfenix on 2009-04-29
abans de tornar enrera, us comento.

ahir vaig aconseguir conectar-me durant una estona, la conexio va ser correcta, pero en mdo adhoc.
en comptes de clau WEP, vaig dir WPA i va tragar, pero no podia navegar, al edita la conexio, vaig veure que estava en modo ad hoc, al cambiaro a modo infrastuctura, no vaig se capaç de fer conexio, per que simplement, no en surt a la llista de xarxes i quan dic conexio nova, no surt com una conexio guardada.

igualmente, he decidit deixar el laptop descansant fins aquesta nit, i al router dos del mateix.

el tema, a data d'avui es que pot ser que network manager tingui alguna anomalia i entengui com la seguretat WPA el que realment es WEP.

aquesta nit, repetire el tema, i us dic alguna cosa.

si finalment, tingues que desfer, com ho tinc que fer. hem sembla que ja ho habia fet fa dos dies. 

gracies,

---

### Post by socderafel on 2009-04-29
pero la clau l'has canviat al router com a wpa???

---

### Post by venusfenix on 2009-04-29
buenas,

doncs no, el router encara no l'he tocat.

per aixo, nomes he tocat les condicions de conexio en el laptop.
en comptes de WEP, vaig posar WPA i va funciona, pero es va conectar en mode adhoc, en comptes de infrastructure.

que et sembla?? ho he fet be?

---

### Post by PatrickVogeli on 2009-04-29
la solució a si ho has fet bé es senzilla: podies navegar?

---

### Post by venusfenix on 2009-04-29
buenas,

sembla que podem tancar ja el tema, despres de deixar "reposar" el laptop tot el dia, ha sigut fe un switch ON, i detectar la xarxa, demanar clau WEP, conectar-se i començar a navegar. 

estare uns dies apagan i encenen el laptop i supervisan que es conecta sempre i cada cop.

la senyal ara es del 87% que si fa no fa, es lo correcte.

moltes gracies,

potser necessitava vacances!!

Per cert, nomes un comentari, ara put navegar, se que no puc compara una conexio per cable (mes estable i constant) que una per wifi, pero tinc la sensacio que amb intrepid la conexio wifi anava mes rapid. o es normal que vagi lent durant les primeres conexions??


gracies,

---

### Post by oriolsbd on 2009-04-29
Hola, si vols fer una prova de la velocitat "efectiva" de la teva connexió ves a aquesta pàgina:

[http://www.internautas.org/testvelocidad](http://www.internautas.org/testvelocidad)

Si vols, pots comparar la velocitat que obtens per Ethernet amb la que obtens per Wifi.

Salut!

---

### Post by venusfenix on 2009-04-29
no ha sigut necessari,

us explico, abans, amb intrepid, podia esta a la part mes llunyana del pis i mira algun episodi per seriesyonkis sense cap probleme, ara, va fem recarregues del episodis o entorpeix varies vegades el streaming.

avui, he aconseguit un segon laptop amb intrepid i he posat tots 2 a la part mes llunyana de la cobertura wifi (la pitjor condicio) i he carregat el mateix episodi de House en tots dos episodis, un ha carregat del tiron tot el episodi, sense interrupcions ni res, com ho feia el meu abans, i el meu, ha tigut moltes parades.
o sigui, he mirat l'episodi en el laptop de "prestao".

que pot haber passat??

gracies,

---

### Post by PatrickVogeli on 2009-04-29
tal com ho entenc jo, pots esta fent servir els moduls ath_pci, ath_hal i ath_rate o be els moduls ath5k o ath9k.

Jo no tinc ni idea de quins moduls suporten la teva tarjeta, pero podries provar.

salut!

---

### Post by venusfenix on 2009-04-30
com puc averigur-lo?? que hauria de fer?

gracies,

---

### Post by PatrickVogeli on 2009-04-30
desfes tot el que has fet i enganxan's el resultat de fer lsmod

---

### Post by venusfenix on 2009-04-30
avui el tema va millor, no he fet res, pero va millor, he probat la pagina web, i si ahir donava uns pocs kbs de baixada avui esta sobre 2Mb (conexio de 3Mb), encara que triga una mica en carrega alguna pagina pero va millor.

igualmente, et passo el resultat de lsmod per si veus alguna cosa que pugui ajudar.

gracies,

Module                  Size  Used by
wlan_wep               14592  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
wlan_scan_sta          22912  1 
ath_rate_sample        22400  1 
ath_pci               224960  0 
wlan                  258848  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               339088  3 ath_rate_sample,ath_pci
joydev                 20864  0 
ndiswrapper           250624  0 
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  2 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_pcm_oss            52352  0 
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_timer              34064  2 snd_seq,snd_pcm
snd                    78792  13 snd_hda_intel,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
uvcvideo               69512  0 
sdhci_pci              16896  0 
psmouse                64028  0 
soundcore              16800  1 snd
k8temp                 13440  0 
pcspkr                 11136  0 
compat_ioctl32         18304  1 uvcvideo
nvidia               8106480  36 
ricoh_mmc              12544  0 
sdhci                  27396  1 sdhci_pci
serio_raw              14468  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
usbhid                 47040  0 
forcedeth              68368  0 
ohci1394               42036  0 
ieee1394              108288  2 sbp2,ohci1394
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

---

### Post by PatrickVogeli on 2009-04-30
jo trobo que podries prova de fer:
sudo modprobe -r ath_rate_sample ath_pci
sudo modprobe -r ath_hal
sudo modprobe ath5k

sudo iwlist scan (per veure si trova xarxes).

Si trova xarxes, al network manager, desactiva i tornar a activar la xarxa i mira si t'hi pots connectar.

Si no funciona, reinicies i estas igual que abans.

salut!

---

### Post by PatrickVogeli on 2009-05-10
bones!

Navegant per curiositat he arribat fins aqui:  [http://packages.ubuntu.com/jaunty/amd64/linux-backports-modules-2.6.28-11-generic/filelist](http://packages.ubuntu.com/jaunty/amd64/linux-backports-modules-2.6.28-11-generic/filelist)

Es la llista de moduls nous disponibles per al kernel 28-11-generic que té la jaunty per defecte, i he vist que hi han els ath5k i ath9k.

Vas poder solucionar el teu problema amb la wifi? Igual l'ath5k que hi en aquest paquet et serveix.

---

### Post by papapep on 2009-05-10
Tal i com ja us vaig comentar [aquí]("http://ubuntuforums.org/showpost.php?p=7151095&postcount=15"), amb aquesta mateixa placa amb el mòdul ath5k de la Jaunty, i blacklistejant un parell de mòduls, efectivament em funciona correctament.

Aquí també en parlen: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Tot i això, a l'install d'ahir a Terrassa, de les dues màquines que van venir amb aquest problema una va anar com la seda i l'altra va marxa sense haver-se arreglat. Ambdós eren Acer, i tenien l'Atheros AR242 igual. Misteris de la informàtica...

---

### Post by PatrickVogeli on 2009-05-10
vau provar amb el linux-backports-modules ???

---

### Post by papapep on 2009-05-10
Sips, però tampoc va funcionar....a més, va venir a última hora i ja estavem (com a mínim jo) fets pols i ja teniem les neurones en ralentí. Una pena...

---

### Post by CarlesOriol on 2009-05-11
Eps... que no va funciona per que estaven capturats els repositoris a la xarxa i mancaven els backports!!!!

Vaja... que vam perdre el temps brutalment. (Però el procediment és bo')

---

### Post by papapep on 2009-05-11
No, "hij", no. Que quan vas desaparèixer :P vaig descarregar els paquets directament de packages.ubuntu.com (amb les seves dependències), i no va funcionar. Però és probable que jo ja patinés molt...

---

### Post by CarlesOriol on 2009-05-11
Mmm.... Si', és probable...

---

