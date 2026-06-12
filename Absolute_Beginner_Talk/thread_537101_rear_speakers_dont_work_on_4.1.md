---
title: "rear speakers dont work on 4.1"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-08-28
i have C-media 9739 and Intel ICH5 

on windows i hear all speakers
on Ubuntu only 2 fronts

i must say that this is the only thing which stops me from moving completely to Ubuntu

help plz? (:

Edit
i just downloaded the C-Media Linux's driver
its say in the instructions:
Step 3. Edit your /etc/modules.conf or conf.modules depending on the Distribution
        alias sound-slot-0 cmaudio    
        post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
        pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || :

can i get a translation for Ubuntu system?
thx

---

### Post by asakurax on 2007-08-29
Bump (:

---

### Post by asakurax on 2007-08-29
here is the whole README file
if anyone can help me how to do this instructions on ubnutu ill ge thankfsul

Linux OSS driver for C-Media audio codec (CMI9738, CMI9739, CMI9761)
> 
Notes:
1. This version implements GPIO on/off when active/disactive the driver which used for Mitac.

Features:
1. South Bridge: Intel ICH2/ICH4/ICH5, SiS 7012/7018, VIA 8233/82686, ALI 5451, nVidia nForce, AMD 8111.
2. Full-duplex and multiple applications playback and recording.
4. 16 bits 2/4/6 channels mono/stereo playback.
5. 16 bits stereo recording.
6. Support phone jacks configuration.
7. PCM SPDIF IN/OUT (CMI9739 and CMI9761, recording only support 48 KHz).
8. Support AC3 S/PDIF out (CMI9739 and CMI9761).
9. Support analog hardware copy to rear channel.
10.Support xear mode to swap front and surround speakers output.
   For PCCHIPS LCD PC, you should change the following codes in cmaudio.h:

        // For PCCHIPS LCD PC
        #define FORCE_LINEINASREAR_MODE 1
        #define FORCE_XEAR_MODE 1

        //#define FORCE_LINEINASREAR_MODE 0
        //#define FORCE_XEAR_MODE 0

Known issues:
1. This driver only tested on RedHat 7.3.
2. /dev/sequencer is not supported.
3. In RedHat 8.0, gmix can not select recording source correctly.
   Please use aumix.


Installation:
For driver installation, please follow below steps. 

Step 1. Unzip source code
        tar xzf cmaudio-xxx.tar.gz

Step 2. Complied source code and install
	./install

Step 3. Edit your /etc/modules.conf or conf.modules depending on the Distribution
        alias sound-slot-0 cmaudio    
        post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
        pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || :



Phone Jacks Configuration:
We provide a console mode program, cmconfig.c, in order to let you change jacks' configuration.
please follow below steps.

Step 1. Compiled source code, the source code is also in cmaudio-xxx.tar.gz.
        cc -o cmconfig cmconfig.c

Step 2. Execute and change the settings
        ./cmconfig

---

### Post by asakurax on 2007-08-31
bump
plz?

---

### Post by orange2k on 2007-08-31
Im not at my Ubuntu box right now, but I had the same problem everytime I installed Ubuntu.
All I had to do was doubleclick on the loudspeaker icon in the tray, enter settings and check the box "wave surround" and then turn up the volume in the mixer...
(Im not quite sure if it was wave surround, cause Im not at my home PC right now - but experiment a little bit with checking boxes for different outputs and Im sure youll make it work...)

---

