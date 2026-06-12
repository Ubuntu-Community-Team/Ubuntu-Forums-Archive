---
title: "Kaffeine i TDT"
date: 2010-01-18
forum: Catalan Team
---

### Post by venusfenix on 2010-01-18
buenas,

tinc un acer intel quad core 2 and ubuntu karmic koala.
tinc conectat un stick TDT amb diversity antenna, de la marca pinnacle, i malgrat que es driver es el dibcom 7000PC, mai ha funcionat.
segons comentaris que he trobat, es que encara no es compatible al 100%.

l'altre dia, vaig veure una actualizacio per temes de dvb, i vaig probar, veiem que ara sintonitzava i es podia veure, en altres paraules, que el tema ara si que funciona, pero al dia següent, va deixar de funcionar.

que pot haber pasat?? tant perque fucioni, com perque deixi de funcionar?

gracies,

---

### Post by orestesmas on 2010-01-19
Tens el firmware? fes:

```

ls -l /lib/firmware/ | grep dvb

```

i quina versió del nucli estàs utilitzant?
```

uname -a

```

A veure què surt...

---

### Post by venusfenix on 2010-01-19
buenas,

en teoria si, et paso el resultat:

ls -l /lib/firmware/ | grep dvb

-rw-r--r--  1 root root   32522 2009-12-03 15:00 dvb-fe-cx24116.fw
-rw-r--r--  1 root root   12772 2009-12-03 15:00 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root   17532 2009-12-03 15:00 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root    8518 2009-12-03 15:00 dvb-fe-or51211.fw
-rw-r--r--  1 root root   24478 2009-12-03 15:00 dvb-fe-tda10046.fw
-rw-r--r--  1 root root   12401 2009-11-10 11:21 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  239956 2009-12-03 15:00 dvb-ttpci-01.fw
-rw-r--r--  1 root root   12700 2009-12-03 15:00 dvb-usb-af9015.fw
-rw-r--r--  1 root root   10757 2009-12-03 15:00 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root    9025 2009-12-03 15:00 dvb-usb-bluebird-01.fw
-rw-r--r--  1 jose jose   29955 2009-07-12 22:03 dvb-usb-dib0700-01.fw
-rw-r--r--  1 root root   34306 2009-12-03 15:00 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root   33768 2009-11-10 11:21 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root    9180 2009-12-03 15:00 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root    7558 2009-12-03 15:00 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root    7431 2009-12-03 15:00 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root    3360 2009-12-03 15:00 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root    4286 2009-12-03 15:00 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root   10752 2009-12-03 15:00 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root   10752 2009-12-03 15:00 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root    8480 2009-12-03 15:00 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root   12902 2009-12-03 15:00 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root    8518 2009-12-03 15:00 dvb-usb-wt220u-zl0353-01.fw

i respecte al nucli, l'ultim: 2.6.31-17-generic

espero noticies!!


moltes gracies!!

---

### Post by venusfenix on 2010-01-19
una altre comentari, amb el kaffeine, puc veure la programació d'alguns programes de TDT, pero no puc veure's (ara per ara)
surt un missatge d'error de demultiplexar (?)

---

### Post by venusfenix on 2010-01-26
alguna indicacio o manera d'actuar??

gracies,

---

### Post by ffp on 2010-01-27
Hola,

Prova d'instal·lar linux-firmware-nonfree, alguns firmwares no es carreguen per defecte a Karmic.
No he comprovat que suporti la teva sintonitzadora !

---

### Post by orestesmas on 2010-01-27
> **venusfenix said:**
> alguna indicacio o manera d'actuar??


Perdona, vaig respondre un dia i després he "abandonat" aquest fil.

La veritat és que, no tenint el teu maquinari, no et puc dir gran cosa. Vaig comprovar quin era el firmware necessari per la teva targeta i vaig trobar que era el dvb-usb-dib0700-1.10.fw (si no recordo malament), i vaig veure que tu el tenies instal·lat, o sigui que no sembla que sigui un problema de firmware.

Podria ser que el nucli no carregui el firmware perquè no reconegui el dispositiu. Fes el següent:

1) Obre una finestra de terminal i executa-hi l'ordre 'dmesg'. Veuràs tota una sèrie de línies informatives.
2) Endolla el dispositiu i torna a executar l'ordre 'dmesg'. Ara la sortida serà la mateixa d'abans però amb unes línies addicionals referents a com el kernel ha detectat el nou dispositiu. Copia-les aquí. Ha de ser quelcom del tipus:

```

usb 3-5: new high speed USB device using ehci_hcd and address 7
usb 3-5: new device found, idVendor=2304, idProduct=0236
usb 3-5: new device strings: Mfr=1, Product=2, SerialNumber=3
usb 3-5: Product: Pinnacle 72e
usb 3-5: Manufacturer: LITEON
usb 3-5: SerialNumber: 10K
usb 3-5: configuration #1 chosen from 1 choice
dvb-usb: found a 'Pinnacle PCTV 72e' in cold state, will try to load a firmware
dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
dib0700: firmware started successfully.
dvb-usb: found a 'Pinnacle PCTV 72e' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Pinnacle PCTV 72e)
DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
DiB0070: successfully identified
input: IR-receiver inside an USB DVB receiver as /class/input/input1
dvb-usb: schedule remote query interval to 50 msecs.
dvb-usb: Pinnacle PCTV 72e successfully initialized and connected.

```

Una vegada fet això, i sense desendollar el dispositiu, també pot ser útil la sortida de les dues ordres següents (serveixen per fer un llistat dels drivers carregats i per saber com el sistema ha reconegut els dispositius USB):

```

lsmod

lsusb
lsusb -t

```

Una vegada sapiguem quin ID té el dispositiu USB podrem buscar a veure si efectivament en connectar-lo s'activa alguna ordre per enviar-li el firmware.

En qualsevol cas, una pàgina que et pots mirar (si no ho has fet ja) és [http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_72e](http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_72e)

---

### Post by venusfenix on 2010-01-27
aqui tens el resultat de dmesg, despres de conectar el usb:

usb 1-2: new high speed USB device using ehci_hcd and address 6
usb 1-2: configuration #1 chosen from 1 choice
dvb-usb: found a 'Pinnacle PCTV 2000e' in cold state, will try to load a firmware
usb 1-2: firmware: requesting dvb-usb-dib0700-1.20.fw
dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
dib0700: firmware started successfully.
dvb-usb: found a 'Pinnacle PCTV 2000e' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Pinnacle PCTV 2000e)
DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
MT2266: successfully identified
 dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
 DVB: registering new adapter (Pinnacle PCTV 2000e)
 DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
 MT2266: successfully identified
 input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-2/input/input9
 dvb-usb: schedule remote query interval to 50 msecs.
 dvb-usb: Pinnacle PCTV 2000e successfully initialized and connected.

---

### Post by venusfenix on 2010-01-27
sortida de lsmod:

Module                  Size  Used by
binfmt_misc             8356  1 
ipt_MASQUERADE          2204  1 
iptable_nat             5500  1 
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  4 iptable_nat,nf_nat
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
xt_state                1820  1 
nf_conntrack           67608  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2812  2 
xt_tcpudp               2780  4 
bridge                 47952  0 
stp                     2272  1 bridge
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
kvm_intel              43816  0 
kvm                   162624  1 kvm_intel
mt2266                  5056  2 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
joydev                 10240  0 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_seq_midi            6432  0 
iptable_filter          3100  1 
snd_rawmidi            22208  1 snd_seq_midi
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ppdev                   6688  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
wacom                  22276  0 
dvb_usb_dib0700        40836  0 
dib7000p               16676  3 dvb_usb_dib0700
dib7000m               14560  1 dvb_usb_dib0700
ip_tables              11692  2 iptable_nat,iptable_filter
x_tables               16544  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
lp                      8964  0 
dvb_usb                16200  1 dvb_usb_dib0700
led_class               4096  0 
dvb_core               87364  1 dvb_usb
dib3000mc              12196  1 dvb_usb_dib0700
dibx000_common          3328  3 dib7000p,dib7000m,dib3000mc
dib0070                 7616  1 dvb_usb_dib0700
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_piix4               9932  0 
shpchp                 32272  0 
vesafb                  5696  0 
usb_storage            52576  0 
floppy                 54916  0 
ohci1394               29900  0 
sky2                   46528  0 
ieee1394               86596  1 ohci1394
usbhid                 38208  0 
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp

---

### Post by venusfenix on 2010-01-27
sortida de lusb:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 2304:022c Pinnacle Systems, Inc. [hex] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 056a:0060 Wacom Co., Ltd 
Bus 003 Device 003: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


i de lusb -t:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 2304:022c Pinnacle Systems, Inc. [hex] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 056a:0060 Wacom Co., Ltd 
Bus 003 Device 003: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by venusfenix on 2010-01-27
referent al teu comentari, si, ja havia mirat aquesta pagina, pero no estic massa possat en aquest temes, amb lo qual, tota ajuda es bona.

moltes merces!!

---

### Post by orestesmas on 2010-01-28
> **venusfenix said:**
> aqui tens el resultat de dmesg, despres de conectar el usb:

usb 1-2: new high speed USB device using ehci_hcd and address 6
usb 1-2: configuration #1 chosen from 1 choice
dvb-usb: found a 'Pinnacle PCTV 2000e' in cold state, will try to load a firmware
usb 1-2: firmware: requesting dvb-usb-dib0700-1.20.fw
dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
dib0700: firmware started successfully.
(...)

A veure: En aquest missatge teu i els següents s'aprecia que el nucli reconeix perfectament el dispositiu, detecta que cal enviar-li el firmware (cold state), li envia, l'altre el rep correctament i s'activa (warm state). Tot això és correcte, i indica que vas pel bon camí.

Ara faltaria comprovar si el teu dispositiu apareix a /dev/dvb com un "adapter0" o qualsevol altre número.

Però vaja, sabent tot això no veig motiu pel qual no aparegui, per la qual cosa ara voldria saber què et passa exactament:

- Quin programa utilitzes (vas dir el kaffeine, oi?)
- Has sintonitzat els canals de Collserola (o de la teva àrea geogràfica corresponent)?
- Si, malgrat tot, el kaffeine no et funciona, has provat amb altres programes?

Respecte això últim et remeto a un conjunt d'utilitats bàsiques que es poden trobar dins el paquet "dvb-apps". Instal·la-te'l i segueix els consells d'aquesta pàgina: [http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device).

En acabar, digues què tal.

---

### Post by orestesmas on 2010-01-28
Ah, i per no haver de preguntar-ho després, pots enganxar la sortida de 
```

ls -l /dev/dvb/adapter0

```

i comprovar que el teu usuari pertany a un grup amb permisos per usar el dispositiu dvb (usualment "video"):

```

groups

```

---

### Post by venusfenix on 2010-02-08
Buenas, i perdona aquest temps que no he respons, pero he estat amb obres a casa, i .... (i quina feinada netejar?!!)

respecte a les teves preguntes; he utilizat entre altres el kaffeine, tambe el MeTV, i tot igual  de be o malament, quan diu funcionar, tot OK, quan no, doncs res.

tinc configurat tot els canals de collserola.

respected a la sortida que em demanes, o fare en un altre post.

moltes gracies,

---

### Post by venusfenix on 2010-02-08
ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 0 2010-02-08 08:12 demux0
crw-rw----+ 1 root video 212, 1 2010-02-08 08:12 dvr0
crw-rw----+ 1 root video 212, 3 2010-02-08 08:12 frontend0
crw-rw----+ 1 root video 212, 2 2010-02-08 08:12 net0


groups
jose adm dialout cdrom plugdev lpadmin admin sambashare mythtv libvirtd

---

### Post by orestesmas on 2010-02-09
> **venusfenix said:**
> ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 0 2010-02-08 08:12 demux0
crw-rw----+ 1 root video 212, 1 2010-02-08 08:12 dvr0
crw-rw----+ 1 root video 212, 3 2010-02-08 08:12 frontend0
crw-rw----+ 1 root video 212, 2 2010-02-08 08:12 net0


groups
jose adm dialout cdrom plugdev lpadmin admin sambashare mythtv libvirtd

Em sembla que aquí hi pot haver el problema: Fixa't que només el root i els usuaris que pertanyen al grup "video" tenen permís per obrir els dispositius, mentre que el teu usuari "jose" no pertany al grup "video".

Per arreglar-ho hi ha diverses maneres però la més simple és afegir tel teu usuari (i tots els que han de poder utilitzar el dispositius) al grup video:

```

sudo adduser jose video

```

Per tal de fer efectius els canvis **recorda que has de sortir de la sessió i tornar a entrar**.

A veure si xuta.

---

### Post by venusfenix on 2010-02-10
buenas.,
i gracies per la resposta,
encara no he fet la proba, pero donaré el "feedback" pertinent.

nomes una pregunta, fins ara, no sabia res del tema grups, aixo pot explicar perque a vegades funcionaba i a vegades no?

---

### Post by venusfenix on 2010-02-14
primera prova i sembla que tot funciona molt be

moltes merces!!!!!!



gracies!!

---

