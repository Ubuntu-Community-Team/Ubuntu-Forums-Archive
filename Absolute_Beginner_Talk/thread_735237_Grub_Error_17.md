---
title: "Grub Error 17"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by smartygoldenfish on 2008-03-25
I installed ubuntu with my dear Bill gates's Windows xp..ofcourse Dual Boot..yesterday

everything worked fine but today when i started it for no reason computer gave GRUB ERROR 17
and hanged!

i pressed CTRL Alt del and put the Windows xp Bootable CD on it (to reapair mbr)
but it threw **PRESS ANY KEY TO BOOT FROM CD...**and then a good blank screen after pressing **any key**

then using live cd i reinstalled ubuntu in the same partition and swap..i am currently working on it.
But why did i happen? If such errors crop up in ubuntu without any reason..why Ubuntu considered to be so **stable**

gates did a better job then bcoz his windows doesnt hang (ONLY at booting) :)

seriously whats the reason for it, i googled and got nothing
how can i prevent it in future?

Also i have a Portable HDD and when i remove it without telling windows, ubuntu doesnt mount it! Why! how can i use that FORCE MOUNT option?

---

### Post by phidia on 2008-03-25
There are actually a great many hits for [grub error 17]("http://www.google.com/search?q=grub+error+17+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")
It could be that your bios is changing the partition order. After an install it always good to do a restart to see if grub and the computer bios is playing well together.
What type of filesystem is the portable drive using? If it's ntfs you can search that at the forums to find solutions for mounting it. If it's something else then post the output of "fdisk -l"

---

### Post by prshah on 2008-03-25
> **smartygoldenfish said:**
> 
everything worked fine but today when i started it for no reason computer gave GRUB ERROR 17
and hanged!

Also i have a Portable HDD and when i remove it without telling windows, ubuntu doesnt mount it! Why! how can i use that FORCE MOUNT option?

Grub error 17 means it has found your partition but cannot mount it. If it ever happens again, try booting from a live CD and ```
sudo fsck /dev/hda1
``` where /dev/hda1 is whatever your linux partition is.

Usually it will mean an unclean shutdown though that shouldn't matter with ext3... sigh.

If you do not cleanly unmount your USB drive in either Windows (Safely Remove device) or Ubuntu (sudo umount device) you are risking data loss and corruption. If you want to use the --force option, you can ```
sudo mount --force /dev/yourdevice
``` but THIS IS NOT RECOMMENDED for various reasons, and it WILL LEAD TO DATA LOSS (experience yelling here, not me.)

---

### Post by xaco1234 on 2008-03-25
when i had error 17 i just had removed the partisiption with windows, i coud allways have booted an live cd, but i was ofcorse stupid enouh to reinstall everything,

---

