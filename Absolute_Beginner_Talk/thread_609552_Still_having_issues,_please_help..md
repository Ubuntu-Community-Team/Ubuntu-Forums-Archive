---
title: "Still having issues, please help."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by thepocketdrummer on 2007-11-11
I have a few different problems that are really bothering me.

First, whenever I log in, my screen resolution is set to 1600x900 or something weird like that. My native resolution is 1680x1050 @ 60Hz. I have to go to System - Administration - Screen and Graphics and set it to 1680x1050, then ctrl+alt+backspace for it to work at the correct resolution.

Is there a way to just make it 1680x1050 right off the bat?

The second issue is sound. I'm having a LOT of trouble getting the Creative X-Fi beta drivers to work. I have 64-bit Ubuntu, but it still doesn't seem to work. If anyone could give me a step by step that would REALLY help.

and last but not least, I can't seem to delete files that are in my recycling bin.

it says,
```
"/home/pocke...-1.04/libs" cannot be deleted because you do not have permissions to modify its parent folder.
```

How can I delete this file?

---

### Post by Partyboi2 on 2007-11-11
```
sudo rm -rf $HOME/.Trash/
```should delete your trash.
as for the screen 1680x1050 problem you could see if this tread helps:

[http://ubuntuforums.org/showthread.php?p=248755](http://ubuntuforums.org/showthread.php?p=248755)

:)

---

### Post by thepocketdrummer on 2007-11-11
The trash one worked. Do I have to type that in every time? (and the icon still looks full but nothing is in it. Is that normal?)

The screen already showed 1680x1050. I'll have to restart to see if it stays that way.

Oh, and do you know anything about the X-Fi drivers?

---

### Post by Partyboi2 on 2007-11-11
You shouldn't have to do it everytime, only when you have those annoying files that won't delete. The normal way of deleting the trash will get rid of your trash most of the time.

---

### Post by thepocketdrummer on 2007-11-11
> **Partyboi2 said:**
> You shouldn't have to do it everytime, only when you have those annoying files that won't delete. The normal way of deleting the trash will get rid of your trash most of the time.

Do you know how to get these X-fi drivers to work? At the moment, I have no sound at all :(

---

### Post by Partyboi2 on 2007-11-11
Have you tried this trouble shooting:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by thepocketdrummer on 2007-11-11
```
HOWTO build X-Fi Modules with gcc 4, kernel 2.6.22

Sucessfull builds :
- gcc version 4.2.1 (Debian 4.2.1-5) - Debian unstable - 2.6.22-amd64 (Debian)
  Asus P5B, Core 2 Duo 6420, Sound Blaster X-Fi Platinum 
- gcc version 4.1.2 (Gentoo 4.1.2) - gentoo - 2.6.22.8 (Vanilla)  

- gcc version 4.1.2 (Debian 4.1.2-16) - Debian testing - 2.6.21-amd64 (Debian)
  Asus M2N-E, AMD64, Sound Blaster X-Fi XtremeMusic 
- gcc version 4.1.2 (Gentoo 4.1.2) - gentoo - 2.6.22-gentoo-r5 (Gentoo)
  Dell Dimension 9200 (DXP061), Sound Blaster X-Fi XtremeMusic (D) Dell variant

+------------------------------------------+
| Preparing the system                     |
+------------------------------------------+

On Debian/Ubuntu, stock kernel :
# apt-get install module-assistant
# m-a prepare
# m-a update

Others distributions, check if you have the following options enabled:
CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_PCM_OSS_PLUGINS=y
CONFIG_SND_SEQUENCER_OSS=y
CONFIG_SND_RTCTIMER=m
CONFIG_SND_SEQ_RTCTIMER_DEFAULT=y
CONFIG_SND_SUPPORT_OLD_API=y

CONFIG_SND_VIRMIDI=m

CONFIG_SOUND_VMIDI=m

CONFIG_SND_EMU10K1=m

+------------------------------------------+
| Building the driver :                    |
+------------------------------------------+

- download driver from creative : http://www.creative.com/language.asp?sDestUrl=/support/downloads
- download http://olausson.de/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch somewhere.
	   http://blackbox.lostwave.net/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch (mirror)
- log as root

# tar -xvzf XFiDrv_Linux_US-1.04.tar.gz XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
# tar -xvjf XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
# chmod -R 755 XFiDrv_Linux_US-1.04
# find XFiDrv_Linux_US-1.04/ -exec touch -c {} \;
# patch -p0 < XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch
# cd XFiDrv_Linux_US-1.04
# ./configure
# make
# make install

enjoy !

+------------------------------------------+
| FAQ :                                    |
+------------------------------------------+

Q: dmesg shows "ctalsa: Unknown symbol malloc_sizes" and the thing stops here.  
A: Your kernel is compiled with SLUB. But SLAB is required because of malloc_sizes which is not in SLUB. 
---> Rebuild your Kernel with SLAB 

Q: dmesg shows "Unknown symbol __stack_chk_fail" and the thing stops here.
A: you need -fno-stack-protector" to CFLAGS
---> edit Makefile.conf and add -fno-stack-protector" to CFLAGS

Q: during "make install" I get: "./ctsound: 35: Syntax error: Bad substitution" 
A: If you are using Debian/ubuntu, your /bin/sh probably point to /bin/dash. 
---> Edit ctsound and change #!/bin/sh to #!/bin/bash
```

If you know of an easier way, please let me know. I run into the "./ctsound: 35: Syntax error" but changing the text doesn't seem to resolve the issue.

---

### Post by thepocketdrummer on 2007-11-11
After I alter ctsound and make / make install, it gives me this:

```
root@TheFridge:/home/pocketdrummer/XFiDrv_Linux_US-1.04# make install
Copy module files...
Update module dependency relationships...
Warning: Can't not find blacklist file /etc/hotplug/blacklist
Install libs...
Install database files...
tar: creative/data/ctp073aw.dat: time stamp 2009-09-17 04:25:02 is 58394520.108699547 s in the future
tar: creative/data/ctp055aw.dat: time stamp 2009-09-17 04:25:01 is 58394519.078815738 s in the future
tar: creative/data/ctp046aw.dat: time stamp 2009-09-17 04:25:00 is 58394518.074771926 s in the future
tar: creative/data: time stamp 2009-09-17 04:25:30 is 58394548.065297716 s in the future
tar: creative/ct_reg.dat: time stamp 2009-09-17 03:58:22 is 58392920.062112453 s in the future
Create device node files...
/dev/emupia already exixts
/dev/x-fi already exists
Install script files...
/etc/init.d/ctsound already exists. Overwrite it...
WARNING: Error inserting ctossrv (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@TheFridge:/home/pocketdrummer/XFiDrv_Linux_US-1.04#
```

---

### Post by Partyboi2 on 2007-11-11
> Q: dmesg shows "Unknown symbol __stack_chk_fail" and the thing stops here.
A: you need -fno-stack-protector" to CFLAGS
---> edit Makefile.conf and add -fno-stack-protector" to CFLAGS Type:
```
dmesg
```Have a look through it and see if you get a error message something like:

```
[1614.223806] ctossrv: Unknown symbol __stack_chk_fail [1614.226499] emupia: Unknown symbol InterlockedIncrement [1614.226538] emupia: Unknown symbol heap_alloc [1614.226571] emupia: Unknown symbol stack_free_page [1614.226632] emupia: Unknown symbol stack_alloc [1614.226703] emupia: Unknown symbol get_ossrv [1614.226734 ] emupia: Unknown symbol unload_all_plugins [1614.226767] emupia: Unknown symbol stack_alloc_page [1614.226798] emupia: Unknown symbol ioctl_dispatch [1614.226829] emupia: Unknown symbol heap_free [1614.226894] emupia: Unknown symbol InterlockedDecrement [1614.226927] emupia: Unknown symbol stack_free [1614.228581] ctsfman : Unknown symbol heap_alloc [1614.228696] ctsfman: Unknown symbol get_ossrv [1614.228729] ctsfman: Unknown symbol ioctl_dispatch [1614.228760] ctsfman: Unknown symbol heap_free [1614.234641] ct20xut: Unknown symbol InterlockedIncrement [1614.234683] ct20xut: Unknown symbol __stack_chk_fail [1614.234713] ct20xut: Unknown symbol heap_alloc [1614.234749] ct20xut: Unknown symbol unregister_plugin [1614.234792] ct20xut: Unknown symbol heap_free [1614.234835] ct20xut: Unknown symbol register_plugin [1614.234864] ct20xut: Unknown symbol InterlockedDecrement [1614.248282] ctexfifx: Unknown symbol InterlockedDecrement [1614.248327] ctexfifx: Unknown symbol register_plugin [1614.248368] ctexfifx: Unknown symbol unregister_plugin [1614.248403] ctexfifx: Unknown symbol __stack_chk_fail [1614.248456] ctexfifx: Unknown symbol heap
```If you get a similar dmesg then you need to edit the Makefile.conf and add
```
-fno-stack-protector
```to CFLAGS

See if that helps :)

---

