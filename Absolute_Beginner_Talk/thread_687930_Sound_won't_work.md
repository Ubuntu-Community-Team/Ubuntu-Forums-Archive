---
title: "Sound won't work"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Picatta on 2008-02-04
I've installed ubuntu 7.10 on my laptop, and installed restricted drivers for modem/wireless (Everything works).  The problem is that there is no sound.

It looks like it SHOULD work, I can change the volume (both with the hardware knob thing and with the icon in the taskbar), but no sound comes out.  Here is the output from lspci.

> 
~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


Also, here are the cards it detects
> 
~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 10
 1 [Modem          ]: ICH-MODEM - Intel 82801DB-ICH4 Modem
                      Intel 82801DB-ICH4 Modem at irq 10


Any ideas?

---

### Post by Picatta on 2008-02-04
I saw on a gentoo wiki that to get this multimedia card working (although on a different laptop) I should enable the intel8x0 modules..

The laptop, btw, is a gateway 4026gz

---

### Post by Picatta on 2008-02-04
bamp

---

### Post by cdtech on 2008-02-04
Check:
```
cat /etc/modprobe.d/alsa-base
```

And:
```
lsmod | grep snd
```

---

### Post by Picatta on 2008-02-04
Your first command:
> 
$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
alex@alex-desktop:/media/disk-1/storage/stuff$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


And the second:
> 
f$ lsmod | grep snd
snd_rtctimer            4384  1 
snd_hda_intel         263840  1 
snd_pcm_oss            44928  0 
snd_pcm                80644  2 snd_hda_intel,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33792  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55172  12 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


---

### Post by cdtech on 2008-02-04
Type in terminal:
```
alsamixer
```
and make sure that none of the controls are muted, ie........
[ATTACH]58742[/ATTACH]

---

### Post by spiderbatdad on 2008-02-04
just to make sure. Is this the only user account? And in```
alsamixer
```are master and pcm both up?

---

### Post by cdtech on 2008-02-04
> **spiderbatdad said:**
> just to make sure. Is this the only user account? And in```
alsamixer
```are master and pcm both up?

What do you mean "user account".  This would be global, for the entire system.

Yes, both are up and if you hit f5 and use your arrow key's to select which volume you want to adjust, then use your "m" key to mute or unmute.

---

### Post by spiderbatdad on 2008-02-04
not necessarily. if another user account is created, under properties>>user privileges in users and groups...use audio devices is an option, as is use cdrom, etc.

---

### Post by Picatta on 2008-02-04
Yes, in fact I turned all of the controls up all the way on all devices, and the speakers don't even make a peep.

EDIT: Also, this was the user account created by ubuntu (has sudo access), and has the ability to use audio.  What I don't get is that the card is detected, the driver is installed, the volume is up, the user has audioa ccess, and still no sound ???

---

### Post by spiderbatdad on 2008-02-04
of course if you right click on the volume applet in the notification panel...mute is not checked?

---

### Post by cdtech on 2008-02-05
Just looking at the modules list I think your sound module is the snd-intel8x0.  Type in a terminal:
```
sudo modprobe snd-intel8x0
```
and see if you get sound for the current session.

---

### Post by Picatta on 2008-02-05
I just searched the forum, and it looks like others have this problem, and it has never been solved

:/

This sucks

---

### Post by spiderbatdad on 2008-02-05
it may yet be solvable. Try ```
asoundconf list
``` Then ```
asoundconf set-default-card XXXXX
``` where XXXXX is whatever the previous command output was. I will try find a link for you on configuring difficult sound cards.

---

### Post by Picatta on 2008-02-05
> laptop:~$ sudo modprobe snd-intel8x0
laptop:~$ asoundconf list
Names of available sound cards:
I82801DBICH4
Modem
laptop:~$ asoundconf set-default-card I82801DBICH4


It still doesn't work :/

---

### Post by spiderbatdad on 2008-02-05
you would need to restart

---

### Post by Picatta on 2008-02-05
I did, but nothing happened.

Also, shouldn't loading kernel modules via modprobe be instant?

---

### Post by cdtech on 2008-02-05
> **Picatta said:**
> I did, but nothing happened.

Also, shouldn't loading kernel modules via modprobe be instant?

yes....

---

### Post by spiderbatdad on 2008-02-05
again not necessarily. there is a blacklisted snd_intel8x0m in /etc/modprobe.d/blacklist....apparently blacklisted because it "doesn't seem to do much" maybe try commenting it out. Also this card should work. We must be missing something simple.

And does ```
/sbin/lsmod
```show the module listed

---

### Post by Picatta on 2008-02-05
I just tried removing the blacklist and modprobing it, but still no dice..

---

### Post by spiderbatdad on 2008-02-05
This is the part where you say, "ooops, I had the volume down." J/K I know you must be bummed. There is a newer version of Alsa. maybe look into it. I'm stumped.[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

There are also some additional alsa packages in synaptic.

---

### Post by cdtech on 2008-02-05
Looking at your sound module list on the first page I don't see the proper modules for your sound card.

If you go to the alsa source directory:
```
/usr/src/alsa/alsa-driver (**or whatever your driver directory is named**)
```
Do:
```
./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install
```

reboot

I had to recompile mine the same way to get it to work right.

---

### Post by spiderbatdad on 2008-02-05
+1 This looks really good. I would love to be able to find that directory with the configure and make file in it. I find drivers in /usr/src/linux-headers-2.6.22-14/sound/drivers/  but no where a configuration file.

---

### Post by cdtech on 2008-02-05
You could use the information I posted here:
[[COLOR="DarkRed"]Installing alsa[/COLOR]]("http://ubuntuforums.org/showthread.php?t=673628&page=4")

---

### Post by spiderbatdad on 2008-02-05
this is what I came up with:[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ObjectAgnosia on 2008-03-25
I'm currently running a 4026gz with 7.10.  To get the sound to work, goto "Volume Control" and make sure "External Amplifier" is unchecked.  Enjoy:)

---

