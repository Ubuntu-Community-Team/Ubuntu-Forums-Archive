---
title: "Controlador para S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
date: 2008-04-02
forum: Argentina Team
---

### Post by Peladorra on 2008-04-02
Buenas. Gracias por adelantado. Soy usuario reciente e inexperto. Tengo problemas varios con la placa de video y supongo que es porque el controlador que se instala por defecto es un genérico. Mi placa de video es una  S3 Inc. VT8375 [ProSavage8 KM266/KL266] y ubuntu la detecta correctamente, pero me propone un controlador genérico y supongo que ese es el problema. He investigado bastante y no encuentro solución, por lo menos no una que entienda. ¿Puede alguien ayudarme? Gracias.

---

### Post by User21 on 2008-04-03
En una terminal, fijate que sale en el apartado de VGA, al hacer:
```
lspci
```
Con eso vamos a poder ayudarte mejor.

---

### Post by Peladorra on 2008-04-04
Muchas Gracias!!!
Te copio el lspci entero: 

julian@julian-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Espero ansioso

---

### Post by User21 on 2008-04-06
Checa si tenes cargado el modulo [prosavage_smbus]("http://hardware4linux.info/module/prosavage_smbus/")  haciendo en una consola
```
lsmod
```

Fijate si [ESTO]("http://www.backports.ubuntuforums.org/showthread.php?t=489442") puede ayudarte...

---

### Post by Peladorra on 2008-04-06
Gracias por contestar, te cuento:

1) el resultado de lsmod indica que no tengo instalado el modulo prosavage_smbus. El resultado es este:

julian@julian-desktop:~$ lsmod
Module                  Size  Used by
xt_limit                3584  8
ipt_LOG                 7552  8
ipt_MASQUERADE          4608  0
ipt_TOS                 3200  0
ipt_REJECT              5760  1
nf_conntrack_irc        8088  0
nf_conntrack_ftp       11136  0
xt_state                3456  6
xt_TCPMSS               5888  0
xt_tcpmss               3200  0
xt_tcpudp               4224  10
pppoe                  15680  2
pppox                   4872  1 pppoe
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0
speedstep_lib           6404  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9612  0
cpufreq_userspace       5280  0
cpufreq_stats           7232  0
cpufreq_conservative     8072  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sbs                    19592  0
button                  8976  0
video                  18060  0
ac                      6148  0
container               5504  0
dock                   10656  0
battery                11012  0
af_packet              24840  2
ppp_generic            29332  6 pppoe,pppox
slhc                    7552  1 ppp_generic
sg                     36764  0
lp                     12580  0
snd_via82xx            29336  1
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401              9640  0
snd_mpu401_uart         9600  2 snd_via82xx,snd_mpu401
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
psmouse                39952  0
serio_raw               8068  0
analog                 13344  0
snd                    54660  14 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
gameport               16776  2 snd_via82xx,analog
pcspkr                  4224  0
i2c_prosavage           5248  0
i2c_algo_bit            7428  1 i2c_prosavage
usblp                  15104  0
via_ircc               27668  0
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
soundcore               8800  1 snd
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
i2c_viapro             10004  0
i2c_core               26112  3 i2c_prosavage,i2c_algo_bit,i2c_viapro
shpchp                 34580  0
via_agp                11264  1
pci_hotplug            32704  1 shpchp
agpgart                35016  1 via_agp
ipv6                  273892  10
evdev                  11136  4
iptable_nat             8708  0
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0
iptable_filter          3968  1
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  11 xt_limit,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_nat,ip_tables
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0
cdrom                  37536  1 ide_cd
ide_disk               18560  4
ata_generic             8452  0
libata                125168  1 ata_generic
scsi_mod              147084  2 sg,libata
floppy                 60004  0
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
via_rhine              25992  0
mii                     6528  1 via_rhine
uhci_hcd               26640  0
usbcore               138632  3 usblp,uhci_hcd
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor
julian@julian-desktop:~$

2) Trate de cargar el modulo con insmod prosavage_smbus, pero evidentemente me falta algún parámetro porque no pasa nada. Quizá puedas orientarme un poco más en como hacer estos, que supongo es la solución, ya que mi targeta de video aparece como soportada por este modulo.

3) Las instrucciones que me mandaste en [http://www.backports.ubuntuforums.org/showthread.php?t=489442](http://www.backports.ubuntuforums.org/showthread.php?t=489442) para usar dpkg-reconfigure en non-graphic mode, las había encontrado antes, y las traté de seguir, pero con el resultado de que deje de ver la pantalla y me vi obligado a reinstalar para salir del lio porque no sabía como arreglarlo. Cuando corre dpkg-reconfigure las opciones que se presentan son muchas más que las que indica el instructivo ese, y los valores por defecto no siempre están.

Gracias otra vez.

---

