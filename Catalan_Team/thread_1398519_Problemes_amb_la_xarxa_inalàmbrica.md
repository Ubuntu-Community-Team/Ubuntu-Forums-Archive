---
title: "Problemes amb la xarxa inalàmbrica"
date: 2010-02-04
forum: Catalan Team
---

### Post by socderafel on 2010-02-04
Hola a tots!!! Ja feia temps que no escrivia res...

Resulta que he fet una instal.lació neta d'Ubuntu (9.10), i tinc algún problemeta amb el so i amb la wifi.
La wifi es connecta correctament, però sols em deixa navegar uns segons, inmediatament després comença a perdre paquets i no em deixa fer res... bé, em deixa però tarda una barbaritat, de fet he carregat aquesta pàgina mentre sopava...
He canviat del network-manager al wicd per si de cas, però continua igual. 
tinc una clau WEP de 13 caracters ASCII,i amb el finestres no em donava problemes...
La meua targeta es una D-LINK prou antiga (7 o 8 anys) amb xip 

Ahi va el tema dels paquets: he fet un ping "llarg" per a que es vegen les oscilacions...

```
socderafel@ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=25 ttl=255 time=31.2 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=255 time=2.18 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=255 time=7.56 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=255 time=3.22 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=255 time=116 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=255 time=8.40 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=255 time=4.54 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=255 time=461 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=255 time=6.33 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=255 time=220 ms
64 bytes from 192.168.1.1: icmp_seq=39 ttl=255 time=4.35 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=255 time=308 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=255 time=4.58 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=255 time=4.72 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=255 time=32.3 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=255 time=4.55 ms
64 bytes from 192.168.1.1: icmp_seq=56 ttl=255 time=4.71 ms
64 bytes from 192.168.1.1: icmp_seq=58 ttl=255 time=5.13 ms
64 bytes from 192.168.1.1: icmp_seq=63 ttl=255 time=8.01 ms
64 bytes from 192.168.1.1: icmp_seq=83 ttl=255 time=4.84 ms
64 bytes from 192.168.1.1: icmp_seq=84 ttl=255 time=6.81 ms
64 bytes from 192.168.1.1: icmp_seq=86 ttl=255 time=5.55 ms
64 bytes from 192.168.1.1: icmp_seq=88 ttl=255 time=4.90 ms
64 bytes from 192.168.1.1: icmp_seq=91 ttl=255 time=4.80 ms
64 bytes from 192.168.1.1: icmp_seq=93 ttl=255 time=4.34 ms
64 bytes from 192.168.1.1: icmp_seq=94 ttl=255 time=8.44 ms
64 bytes from 192.168.1.1: icmp_seq=95 ttl=255 time=7.56 ms
64 bytes from 192.168.1.1: icmp_seq=96 ttl=255 time=4.93 ms
64 bytes from 192.168.1.1: icmp_seq=97 ttl=255 time=4.93 ms
64 bytes from 192.168.1.1: icmp_seq=98 ttl=255 time=4.81 ms
64 bytes from 192.168.1.1: icmp_seq=99 ttl=255 time=6.18 ms
64 bytes from 192.168.1.1: icmp_seq=101 ttl=255 time=4.99 ms
64 bytes from 192.168.1.1: icmp_seq=102 ttl=255 time=5.56 ms
64 bytes from 192.168.1.1: icmp_seq=103 ttl=255 time=4.93 ms
64 bytes from 192.168.1.1: icmp_seq=104 ttl=255 time=4.68 ms
64 bytes from 192.168.1.1: icmp_seq=105 ttl=255 time=5.18 ms
64 bytes from 192.168.1.1: icmp_seq=107 ttl=255 time=5.04 ms
64 bytes from 192.168.1.1: icmp_seq=108 ttl=255 time=10.1 ms
64 bytes from 192.168.1.1: icmp_seq=109 ttl=255 time=8.07 ms
64 bytes from 192.168.1.1: icmp_seq=129 ttl=255 time=4.91 ms
64 bytes from 192.168.1.1: icmp_seq=136 ttl=255 time=9.26 ms
64 bytes from 192.168.1.1: icmp_seq=137 ttl=255 time=6.57 ms
64 bytes from 192.168.1.1: icmp_seq=141 ttl=255 time=7.76 ms
64 bytes from 192.168.1.1: icmp_seq=142 ttl=255 time=4.69 ms
64 bytes from 192.168.1.1: icmp_seq=143 ttl=255 time=6.32 ms
64 bytes from 192.168.1.1: icmp_seq=150 ttl=255 time=4.78 ms
64 bytes from 192.168.1.1: icmp_seq=151 ttl=255 time=4.44 ms
64 bytes from 192.168.1.1: icmp_seq=152 ttl=255 time=6.45 ms
64 bytes from 192.168.1.1: icmp_seq=156 ttl=255 time=4.59 ms
64 bytes from 192.168.1.1: icmp_seq=159 ttl=255 time=8.67 ms
64 bytes from 192.168.1.1: icmp_seq=160 ttl=255 time=6.57 ms
64 bytes from 192.168.1.1: icmp_seq=161 ttl=255 time=4.43 ms
64 bytes from 192.168.1.1: icmp_seq=162 ttl=255 time=4.43 ms
64 bytes from 192.168.1.1: icmp_seq=163 ttl=255 time=6.57 ms
64 bytes from 192.168.1.1: icmp_seq=169 ttl=255 time=5.31 ms
64 bytes from 192.168.1.1: icmp_seq=170 ttl=255 time=4.68 ms
64 bytes from 192.168.1.1: icmp_seq=171 ttl=255 time=8.68 ms
64 bytes from 192.168.1.1: icmp_seq=172 ttl=255 time=4.94 ms
64 bytes from 192.168.1.1: icmp_seq=173 ttl=255 time=4.93 ms
64 bytes from 192.168.1.1: icmp_seq=178 ttl=255 time=5.07 ms
64 bytes from 192.168.1.1: icmp_seq=180 ttl=255 time=4.42 ms
64 bytes from 192.168.1.1: icmp_seq=181 ttl=255 time=4.81 ms
64 bytes from 192.168.1.1: icmp_seq=183 ttl=255 time=4.64 ms
64 bytes from 192.168.1.1: icmp_seq=184 ttl=255 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=185 ttl=255 time=4.81 ms
64 bytes from 192.168.1.1: icmp_seq=186 ttl=255 time=4.81 ms
64 bytes from 192.168.1.1: icmp_seq=187 ttl=255 time=5.43 ms
64 bytes from 192.168.1.1: icmp_seq=189 ttl=255 time=12.3 ms
64 bytes from 192.168.1.1: icmp_seq=190 ttl=255 time=5.07 ms
64 bytes from 192.168.1.1: icmp_seq=191 ttl=255 time=6.56 ms
64 bytes from 192.168.1.1: icmp_seq=192 ttl=255 time=4.30 ms
64 bytes from 192.168.1.1: icmp_seq=194 ttl=255 time=4.50 ms
64 bytes from 192.168.1.1: icmp_seq=195 ttl=255 time=4.18 ms
64 bytes from 192.168.1.1: icmp_seq=196 ttl=255 time=4.69 ms
64 bytes from 192.168.1.1: icmp_seq=197 ttl=255 time=4.56 ms
64 bytes from 192.168.1.1: icmp_seq=201 ttl=255 time=8.48 ms
^C
--- 192.168.1.1 ping statistics ---
227 packets transmitted, 76 received, 66% packet loss, time 226989ms
rtt min/avg/max/mdev = 2.183/20.606/461.483/67.145 ms

```

Aqui pego la sortida de lsmod: 

socderafel@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_realtek   203328  1 
rt2500usb              21152  0 
rt2x00usb              11548  1 rt2500usb
iptable_filter          3100  0 
rt2x00lib              29756  2 rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
ppdev                   6688  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
ip_tables              11692  1 iptable_filter
snd_hwdep               7200  1 snd_hda_codec
x_tables               16544  1 ip_tables
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
psmouse                56500  0 
serio_raw               5280  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
cfg80211               93052  2 rt2x00lib,mac80211
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             31940  1 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
ohci1394               29900  0 
r8169                  32064  0 
mii                     5212  1 r8169
usb_storage            52576  2 
ieee1394               86596  1 ohci1394
intel_agp              27484  0 
agpgart                34988  1 intel_agp

Agraïria molt la vostra ajuda...

---

### Post by PatrickVogeli on 2010-02-04
prova a fer sudo iwconfig wlan0 rate 5.5M

a veure si aixi millora

---

### Post by socderafel on 2010-02-04
pareix que si que ha millorat algo, pero segueix perdent almenys el 20% dels paquets... 
ara la navegació es un poc més fluida, però no em carrega videos de megavideo o youtube, per exemple.
M'agradaria saber el que he fet, per a poder jugar amb el comandament. Moltes gràcies!!

---

### Post by papapep on 2010-02-05
> M'agradaria saber el que he fet, per a poder jugar amb el comandament

Si vols saber què fa l'iwconfig pots fer al terminal:

```
man iwconfig
```

o mirar, exactament el mateix, a [aquesta]("http://linux.die.net/man/8/iwconfig") pàgina.

També tens a la teva disposició una completa, i densa, pàgina de help.ubuntu.com sobre xarxes i wifi: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

