---
title: "Power Mac G5"
date: 2006-10-04
forum: Apple PPC Users
---

### Post by xpediant on 2006-10-04
I'm attempting a install of just Ubuntu straight ( No dual boot). I don't have the CD's for OS X so solutions requiring running OS X i've been unable to attempt. The problem is after installation and reboot to run Ubuntu the system hangs on loading second bootloader. A small window pops up alternating with a picture of a question mark and a picture of a outline of two faces (i'm assuming this is a Mac thing). The system then reboots. This cycle continues with the system appearing to run harder with each cycle ( Fans speed up incrementally with each boot.)
The system is a a1047 model G5. 
2.0 dual core processor
160gb HD
single optical drive ( not sure of the model but the optical drive didn't seem to be an issue.)

I'm using the latest Dapper Drake Cds. The install works correctly with the Mac install disc and the x86 disc is not even recognized(tested x86 disc in another PC to make sure it burned correctly). 
I've read up on the Ubuntu forums and the general net. I've used mac-fdisk with the b option to create the bootloader partition. I've used the c option and created a 16MB partition for the bootloader as one forum mentioned the 800K size was not large enough for GRUB.
I've reconfigured yaboot to to see the bootload correctly.
I've run out of ideas as to what is going on  ](*,) and i'm hoping that someone could clue me in. Thanks

---

### Post by stmiller on 2006-10-04
GRUB is for x86 (pc) hardware only. For Macintosh PPC, we use yaboot.

And the x86 CD is for, well, x86 hardware! The powermac G5 is powerpc. So you must use the powerpc CD.

Read here, post #5:

[http://ubuntuforums.org/showthread.php?t=232908&highlight=powermac+g5](http://ubuntuforums.org/showthread.php?t=232908&highlight=powermac+g5)

For how to install on a powermac G5. Note: you must use the alternative powerpc CD, and it is a text based install.

And no need to make a boot partition, etc. Ubuntu installer handles all of that.

---

### Post by kellogs on 2006-10-04
I should add for simplicity, when It asks about partitions, let it handle it automatically, if you loose a few gigabytes in the auto-partitioning dont worry. later you will assign those to space where you can have backups. or you can manage that space with a partition program.

---

### Post by xpediant on 2006-10-05
When using the alternative PPC alternative CD and holding c to boot off the CD all I recieve is a blueish-grey blank screen. The fans slowly speed up to full throttle and stay there. My first thought was trying to get to a different terminal window but with no results. Tried clearing the PRAM as this was indicated to be a possible issue with the video displaying and the bios being confused. I'm still researching answers on this but insight as always is apreciated.

---

### Post by stmiller on 2006-10-05
Hi what happens when you hold the Option key when booting? This should bring you to a boot menu, where you can select the CD.

---

