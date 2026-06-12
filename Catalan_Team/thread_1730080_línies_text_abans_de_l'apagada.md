---
title: "línies text abans de l'apagada"
date: 2011-04-15
forum: Catalan Team
---

### Post by abosch on 2011-04-15
Fa uns dies vaig actualitzar a de 9.10 a 10.04 ... ara quan apago l'ordinador em surt un seguit de línies de text que no tinc temps de llegir, he provat d'aturar-les però tampoc. 


Com podria fer per capturar-les? ... pot ser que en donin algun missatge-error?


gràcies

---

### Post by wgarcia on 2011-04-16
Això molt probablement és degut a què el sistema gràfic senzill que hi ha a l'arrencada i a l'apagada (plymouth) falla degut a la targeta gràfica, i per això el sistema t'ensenya els missatges que normalment estan ocults si funciona la gràfica (la que mostra "Ubuntu" amb uns puntets que es posen vermells). Si tens una NVIDIA és un error conegut i hi ha em sembla algun pegat que ho arregla. Normalment si no veus cap altre efecte, com que el sistema no acaba d'apagar, simplement les línies donen informació que els diferents serveis s'estan tancant abans d'apagar.

---

### Post by kimet on 2011-04-16
Busca el fitxer de logs a /var/log, pot ser user.log, o xorg.0.log.(com a root).

Salut

---

### Post by abosch on 2011-04-18
Gràcies per les respostes, 

aquesta actualització a 10.04 no m'acaba de convèncer. He perdut uns 2 3 seg d'arrencada, em surten missatges quan estic navegant (avís URL no vàlid i no es pot carregar), em falla la hivernació i l'aturada temporal, i potser algun problema amb el sist. gràfic.


Per aquests dos darrers, vaig estar llegint que podria venir per la acpi, que podria desactivar o be descarregar pel sinàptic el paquets relacionats per mirar de solucionar-ho. També vaig llegir pel wiki de la comunitat un article (que ara no trobo) que explicava com mirar de solucionar aquest problema. Què em recomanes per mirar de solucionar-ho? 

Em sembla que no porto Nvidia,
> abosch@abb-ntbk:~$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)



Tot i que quan demano em torna gràfica com a ATI, ?¿

> abosch@abb-ntbk:~$ lspci |grep intel
abosch@abb-ntbk:~$ lspci |grep nvidia
abosch@abb-ntbk:~$ lspci |grep ati
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100



> abosch@abb-ntbk:~$ sudo lshw -c video

  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:90000000-903fffff memory:80000000-8fffffff(prefetchable) ioport:3100(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:92400000-924fffff


@kimet he cercat per el directori que em dius, em sembla que hi tinc masses fitxers. No acabo de veure on cercar-ho. 

Darrerament llegeixo que es recomanable de fer reinstal.lacions del sistema. Creus és necessari?

---

### Post by kimet on 2011-04-18
> @kimet he cercat per el directori que em dius, em sembla que hi tinc masses fitxers. No acabo de veure on cercar-ho. 
En aquest directori s'emmagatzemen els esdeveniments del sistema, hi ha d'haver un fitxer user.log, un xorg.log, dmesg, boot.log, etc on pots buscar errors o informació d'alguna cosa que et falla, no se si per defecte ubuntu guarda logs de l'arrencada, si no es així, en l'arxiu /etc/default/bootlogd, hi escrius: BOOTLOGD_ENABLE=Yes i apareixerà un fitxer boot.log a /var/log.

El dmesg el pots veure simplement fent **sudo dmesg** en un terminal i et donarà informació sobre els dispositius(per veure tots aquest fitxers ha de fer-ho com a superusuari)

> Darrerament llegeixo que es recomanable de fer reinstal.lacions del sistema. Creus és necessari? No, una mala política reinstal.lar quan hi ha un problema.

Un altre aclariment: l'ordre grep retorna un patró.
per tant si fas **grep intel**(en minuscula) no retorna res, prova grep Intel. I si fas grep ati et retorna el que veus perqué hi ha un patró coincident:
00:00.0 Host bridge: Intel Corpor**ati**on Mobile 4 Series Chipset Memory Controller Hub (rev 07):)

Salut.

---

### Post by wgarcia on 2011-04-18
```
grep -i intel
```

ignora majúscules o minúscules

---

### Post by abosch on 2011-04-20
He estat provant amb les recomanacions que m'heu fet; 

l'odre ```
grep -i intel
``` no em retorna res. Es queda com "pensant" i he de tancar el terminal "matant" el procés. 

Pel que fa a l'ordre dmesg la trobo molt interessant; aquest missatge de diagnòstic també inclou possibles errors d'apagada (de l'anterior apagada de la màquina)? He llegit pel wiki que amb un dimoni de registre, com a syslog, es pot registrar al disc dur; a això feies referència quan comentaves ... 

> on pots buscar errors o informació d'alguna cosa que et falla, no se si per defecte ubuntu guarda logs de l'arrencada, si no es així, en l'arxiu /etc/default/bootlogd, hi escrius: BOOTLOGD_ENABLE=Yes i apareixerà un fitxer boot.log a /var/log.



Dintre el user.log he trobat unes indicacions que es van repetint, em sembla entendre que tenen a veure amb l'audio que no hi havia detectat problemes, i d'altres que no entenc (el ressaltat vermell és meu):
 
1/ > 
Apr 18 15:53:43 abb-ntbk [COLOR="Red"]os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2[/COLOR]
Apr 18 15:53:43 abb-ntbk 50mounted-tests: debug: /dev/sda2 is a swap partition; skipping
Apr 18 15:53:43 abb-ntbk os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk 10freedos: debug: /dev/sda3 is not a FAT partition: exiting
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk 10qnx: debug: /dev/sda3 is not a QNX4 partition: exiting
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk macosx-prober: debug: /dev/sda3 is not an HFS+ partition: exiting
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk [COLOR="Red"]20microsoft[/COLOR]: debug: /dev/sda3 is not a MS partition: exiting
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk [COLOR="Red"]30utility: debug: /dev/sda3 is not a FAT partition: exiting[/COLOR]
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda3
Apr 18 15:53:43 abb-ntbk os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda3
Apr 18 16:14:49 abb-ntbk pulseaudio[1496]: ratelimit.c: 6 events suppressed
Apr 18 18:03:35 abb-ntbk pulseaudio[1496]: ratelimit.c: 10 events suppressed
Apr 18 22:23:33 abb-ntbk pulseaudio[1496]: ratelimit.c: 467 events suppressed
Apr 18 22:23:43 abb-ntbk pulseaudio[1496]: ratelimit.c: 466 events suppressed
Apr 18 22:24:24 abb-ntbk pulseaudio[1496]: last message repeated 4 times
Apr 18 22:24:24 abb-ntbk pulseaudio[1496]: ratelimit.c: 78 events suppres


2/> Apr 19 08:50:42 abb-ntbk pulseaudio[1291]: [COLOR="Red"]core-util.c: Home directory /etc/timidity not ours.
Apr 19 08:50:42 abb-ntbk pulseaudio[1291]: lock-autospawn.c: Cannot access autospawn lock.
Apr 19 08:50:42 abb-ntbk pulseaudio[1291]: main.c: Failed to acquire autospawn lock[/COLOR]
Apr 19 08:51:10 abb-ntbk pulseaudio[1465]: alsa-util.c: snd_pcm_avail() ha retornat un valor excepcionalment gran: 3528320 bytes (10000 ms).
Apr 19 08:51:10 abb-ntbk pulseaudio[1465]: alsa-util.c: Probablement es tracta d'un[COLOR="Red"] error del controlador de l'ALSA 'snd_hda_intel'. Informeu d'aquest incident als desenvolupadors de l'ALSA.[/COLOR]
Apr 19 08:51:10 abb-ntbk pulseaudio[1465]: alsa-util.c: snd_pcm_dump():


3/ > Apr 19 12:04:57 abb-ntbk pulseaudio[1482]: alsa-util.c:   hw_ptr       : 24
Apr 19 12:19:45 abb-ntbk pulseaudio[1482]: ratelimit.c: 2 events suppressed
Apr 19 14:13:43 abb-ntbk pulseaudio[1482]: ratelimit.c: 96 events suppressed
Apr 19 18:14:58 abb-ntbk pulseaudio[1293]: core-util.c: Home directory /etc/timidity not ours.
Apr 19 18:14:58 abb-ntbk pulseaudio[1293]: lock-autospawn.c: Cannot access autospawn lock.
Apr 19 18:14:58 abb-ntbk pulseaudio[1293]:[COLOR="Red"] main.c: Failed to acquire autospawn lock[/COLOR]
Apr 19 18:16:22 abb-ntbk pulseaudio[1471]: alsa-util.c: snd_pcm_avail() ha retornat un valor excepcionalment gran: 3528320 bytes (10000 ms).
Apr 19 18:16:22 abb-ntbk pulseaudio[1471]: alsa-util.c: Probablement es tracta d'un error del controlador de l'ALSA 'snd_hda_intel'. Informeu d'aquest incident als desenvolupadors de l'ALSA.
Apr 19 18:16:22 abb-ntbk pulseaudio[1471]: alsa-util.c: snd_pcm_dump():
Apr 19 18:16:22 abb-ntbk pulseaudio[1471]: alsa-util.c: Soft volume PCM


Dintre el Xorg.O.log no hi sé veure errors (si n'hi ha), en tot cas em crida l'atenció

1/> (II) intel(0): [COLOR="Red"]Not using default mode[/COLOR] "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1


Més em sobta dintre el debug ...

1/> Apr 20 14:51:05 abb-ntbk NetworkManager: <debug> [1303303865.261885] ensure_killed(): ppp pid 3028 cleaned up
Apr 20 14:51:06 abb-ntbk modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1
Apr 20 17:35:35 abb-ntbk kernel: [15484.382864] PM: [COLOR="Red"]Preparing system for mem sleep[/COLOR]
Apr 20 17:35:35 abb-ntbk kernel: [15484.384319] PM: Entering mem sleep
Apr 20 17:35:35 abb-ntbk kernel: [15485.776223] [COLOR="Red"]ACPI handle has no context![/COLOR]
Apr 20 17:35:35 abb-ntbk kernel: [15485.865031] [COLOR="Red"]Back to C![/COLOR]
Apr 20 17:35:35 abb-ntbk kernel: [15485.868479] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0x8000000c)

2/> Apr 20 17:36:05 abb-ntbk NetworkManager: [COLOR="Red"]<debug> [1303313765.533378] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyACM0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so[/COLOR]
Apr 20 17:36:05 abb-ntbk NetworkManager: <debug> [1303313765.537874] nm_ppp_manager_start(): ppp started with pid 3855
Apr 20 17:36:06 abb-ntbk kernel: [15519.837729] wlan0: deauthenticating from 00:23:f8:c8:95:3b by local choice (reason=3)

3/> 
Apr 20 20:55:54 abb-ntbk rtkit-daemon[1339]: Sucessfully called chroot.
Apr 20 20:55:54 abb-ntbk rtkit-daemon[1339]: Sucessfully dropped privileges.
Apr 20 20:55:54 abb-ntbk rtkit-daemon[1339]: Sucessfully limited resources.
Apr 20 20:55:54 abb-ntbk [COLOR="Red"]rtkit-daemon[1339]: Running.
Apr 20 20:55:54 abb-ntbk rtkit-daemon[1339]: Watchdog thread [/COLOR]running.
Apr 20 20:55:54 abb-ntbk rtkit-daemon[1339]: Canary thread running.
Apr 20 20:55:54 abb-ntbk rtkit-daemon[1339]: Supervising 1 threads of 1 processes of 1 users.
Apr 20 20:55:55 abb-ntbk rtkit-daemon[1339]: Supervising 2 threads of 1 processes of 1 users.
Apr 20 20:55:55 abb-ntbk rtkit-daemon[1339]: Supervising 3 threads of 1 processes of 1 users.
Apr 20 20:56:06 abb-ntbk rtkit-daemon[1339]: Supervising 4 threads of 2 processes of 2 users.
Apr 20 20:56:06 abb-ntbk rtkit-daemon[1339]: Supervising 5 threads of 2 processes of 2 users.
Apr 20 20:56:06 abb-ntbk rtkit-daemon[1339]: [COLOR="Red"]Supervising 6 threads of 2 processes of 2 users.[/COLOR]
Apr 20 20:56:26 abb-ntbk kernel: [   50.876089] wlan0: deauthenticating from 00:23:f8:c8:95:3b by local choice (reason=3)


Algun d'aquests retorns poden indicar errors?

Gràcies de nou, disculpeu la poca concreció dels missatges, però tinc pocs coneixements i el poc que he anat aprenent, sovint ho he de refrescar per parlar amb una mica de sentit ... i llavors sempre em van apareixent nous interrogants :D




salut

---

### Post by wgarcia on 2011-04-21
El que em referia era a 

dmesg | grep -i intel

(nota que intel a més no porta accent, com em sembla que apareix a la teva resposta)

Els missatge d'advertències i alguns d'error que et surten en les línies que enganxes, no necessàriament impliquen algun malfuncionament, a vegades són missatges que surten per l'ordre de arrencada dels processos i aplicacions. 

La qüestió és, a part dels missatges que menciones, notes algun malfuncionament o el sistema acaba apagant-se sense mes conseqüència?

---

### Post by abosch on 2011-04-22
Ara sí , amb l'ordre ```
dmesg | grep -i intel
``` em retorna informació. 

Errors (o problemes amb 10.04) en continuo tenint, el més molest la fallada amb la hibernació i amb l'aturada temporal. Continuaré cercant informació, i en tot de cas per no barrejar obriré un altre fil. Aquí queda prou clar com trobar els registres a> /var/log

mercès

Salut

---

