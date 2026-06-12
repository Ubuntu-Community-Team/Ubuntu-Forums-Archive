---
title: "WIFI no escaneja"
date: 2009-06-23
forum: Catalan Team
---

### Post by venusfenix on 2009-06-23
Buenas,

torno a tindre els mateixos problemes que quant vaig instal.lar per primer cop jaunty jackalope.
pero primer, lo primer:
tinc un AMD 64bit x 2 amb el jaunty jackalope 64 bits.

ahir mateix es va instal.lar 42 paquets nous, i demanava reiniciar maquina, aquest mati quant l'he ences, ho ha fet tot be, meig la wifi que ni tan sols en diu les wifi's actives que n'hi han, es com tornar quant vaig instal.lar el jaunty per primera vegada.

que em recomaneu? que agafi el post inicial i torni a re-fer tot?

alguna indicacio?

gracies,

---

### Post by venusfenix on 2009-06-24
buenas,

dono mes informacio:
ACER 7520 AMD 64x2 amb JAUNTY
utilitzo el network manager que funcionava correctament amb el kernel 2.6.28-11, al actualitzar-se a 2.6.28-13 ha deixar de funcionar, de tal manera, que ni tan sols scaneja les xarxes, he vist en ubuntuforums americanes que confirmen el probleme pero el sintomes no son els mateixos, nomes diuen que la Wifi els hi deixa de funcionar.

paso copia del resultat de lspci:

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


resultat de ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:1b:38:68:9e:c4  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe68:9ec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2615702 (2.6 MB)  TX bytes:407930 (407.9 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4882 (4.8 KB)  TX bytes:4882 (4.8 KB)

tambe de sudo iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tambe de lsmod


Module                  Size  Used by
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
ath_pci               108400  0 
wlan                  232736  1 ath_pci
ath_hal               225904  1 ath_pci
joydev                 20864  0 
ndiswrapper           250624  0 
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  2 
snd_seq_dummy          11524  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_rawmidi            33920  1 snd_seq_midi
psmouse                64028  0 
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 13440  0 
pcspkr                 11136  0 
nvidia               8106480  36 
serio_raw              14468  0 
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
snd                    78792  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
uvcvideo               69512  0 
compat_ioctl32         18304  1 uvcvideo
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

finalment de dpkg -l (nomes paquest linux...):

rc  linux-backports-modules-2.6.28-11-gene 2.6.28-11.12                           Ubuntu supplied Linux modules for version 2.6.28 on x86/x86_64
ii  linux-backports-modules-2.6.28-13-gene 2.6.28-13.14                           Ubuntu supplied Linux modules for version 2.6.28 on x86/x86_64
ii  linux-backports-modules-jaunty         2.6.28.13.17                           Generic Linux backported drivers.
ii  linux-backports-modules-jaunty-generic 2.6.28.13.17                           Backported drivers for generic kernel image
ii  linux-firmware                         1.11                                   Firmware for Linux kernel drivers
ii  linux-headers-2.6.28-11                2.6.28-11.42                           Header files related to Linux kernel version 2.6.28
ii  linux-headers-2.6.28-11-generic        2.6.28-11.42                           Linux kernel headers for version 2.6.28 on x86/x86_64
ii  linux-headers-2.6.28-13                2.6.28-13.44                           Header files related to Linux kernel version 2.6.28
ii  linux-headers-2.6.28-13-generic        2.6.28-13.44                           Linux kernel headers for version 2.6.28 on x86/x86_64
ii  linux-headers-2.6.29-02062904          2.6.29-02062904                        Header files related to Linux kernel version 2.6.29
ii  linux-headers-generic                  2.6.28.13.17                           Generic Linux kernel headers
rc  linux-image-2.6.24-16-generic          2.6.24-16.30                           Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-18-rt               2.6.24-18.32                           Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.
rc  linux-image-2.6.24-19-generic          2.6.24-19.41                           Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-21-generic          2.6.24-21.43                           Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.27-11-generic          2.6.27-11.31                           Linux kernel image for version 2.6.27 on x86/x86_64
rc  linux-image-2.6.27-7-generic           2.6.27-7.16                            Linux kernel image for version 2.6.27 on x86/x86_64
rc  linux-image-2.6.27-9-generic           2.6.27-9.19                            Linux kernel image for version 2.6.27 on x86/x86_64
ii  linux-image-2.6.28-11-generic          2.6.28-11.42                           Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-13-generic          2.6.28-13.44                           Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-generic                    2.6.28.13.17                           Generic Linux kernel image
ii  linux-libc-dev                         2.6.28-13.44                           Linux Kernel Headers for development
rc  linux-restricted-modules-2.6.24-16-gen 2.6.24.12-16.34                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-18-rt  2.6.24.13-18.41                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-19-gen 2.6.24.13-19.45                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-21-gen 2.6.24.14-21.51                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.27-11-gen 2.6.27-11.16                           Non-free Linux kernel modules for version 2.6.27 on x86/x86_64
rc  linux-restricted-modules-2.6.27-7-gene 2.6.27-7.12                            Non-free Linux kernel modules for version 2.6.27 on x86/x86_64
rc  linux-restricted-modules-2.6.27-9-gene 2.6.27-9.13                            Non-free Linux kernel modules for version 2.6.27 on x86/x86_64
ii  linux-restricted-modules-2.6.28-11-gen 2.6.28-11.15                           Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
ii  linux-restricted-modules-2.6.28-13-gen 2.6.28-13.17                           Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
ii  linux-restricted-modules-common        2.6.28-13.17                           Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic       2.6.28.13.17                           Restricted Linux modules for generic kernels
ii  linux-sound-base                       1.0.18.dfsg-1ubuntu8                   base package for ALSA and OSS sound systems
rc  linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.23                           Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
rc  linux-ubuntu-modules-2.6.24-19-generic 2.6.24-19.28                           Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
rc  linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32                           Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64


m'agradaria saber si es pot fer un "desfer" i tornar al kernel 2.6.28-11 o posar un patch si existis...

moltes merces!!!

---

### Post by papapep on 2009-06-24
> que em recomaneu? que agafi el post inicial i torni a re-fer tot?

si et va funcionar el primer cop, per què no ho proves?

> m'agradaria saber si es pot fer un "desfer" i tornar al kernel 2.6.28-11 o posar un patch si existis...

Sempre pots arrencar amb els nuclis anteriors, si no els has desinstal·lat :)
Quan arrenqui l'ordinador, prem Esc (quan vegis "Press Esc" a la cantonada d'amunt a l'esquerra de la pantalla) i tria amb quina versió de nucli vols arrencar.

---

### Post by venusfenix on 2009-06-24
buenas,

i merces per la ajuda, a mes, em sembla que l'he feta pitjor.

he fet el que jo mateix he dit i que tu recomanes, o sigui, tornar a repetir el tema, pero res

i despres, m'he posat a mirar els ubuntu forums americans i no aconsejaven camviar el kernel a -13 i burru de mi, que llavors, sense saber com va, vaig i descarrego el kernel -30 i pitjor! ara, res amb la nvidia.

aixo, si, acabo de probar el que dius amb el ESC i funciona, i tot!!cap problema.

ara la pregunta es, com desfaig tota la m.r.d. que he montat i jo solet?

es pot fer?

molt agrait!!!! de veritat!!!!

---

### Post by SiscoGarcia on 2009-06-24
Si no has eliminat els nuclis anteriors pots eliminar els nous o bé "comentar-los" (posar-hi # al davant de les línies que en fan referència) al menu.lst del grub (editant el fitxer /boot/grub/menu.lst com a administrador). Si el que vols és eliminar-los fes un:

```
sudo aptitude purge linux-image-versió_del_paquet
```

substituint "versió_del_paquet" per la 2.6.28-13 o la que vulguis eliminar. Pots fer abans un:

```
sudo aptitude search linux-image-|grep ^i
```

per veure quins tens instal·lats i decidir quin/s vols eliminar.

Espero que et serveixi, però ves amb compte.

---

### Post by quitus on 2009-06-26
Hi ha una petita aplicació anomenada startup-manager per poder editar el menu.lst del grub des de un entorn gràfic.


salut

---

