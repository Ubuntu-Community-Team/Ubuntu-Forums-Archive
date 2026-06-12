---
title: "Computer Independant?"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Screwworkn on 2006-02-05
I have a hard drive that I have install the default installation.  Should I be able to move that hard drive and have everything work the same way ala Dos?

Thanks
Chris

---

### Post by atoponce on 2006-02-05
Are you asking if you can reformat the hard drive, and install DOS?  Please clarify, your question is a little vague and difficult to understand.

---

### Post by Screwworkn on 2006-02-05
Sorry if I wasn't clear.  I just want to take the hard drive to another computer and wonder if everything should work the same as it did on the hardware that I installed ubuntu on.  I can do this with dos w/o any issues, windows complains when you change hardware.  Just wondered how linux handled this.

Thanks
Chris

---

### Post by Ocxic on 2006-02-05
so long as the hardware in the 2 macheins are relitivley the same, with no major vendor changes you should be ok. going form AMD to Intel is possible, but intel to AMD will prolly give you problems, plus you'll most likly have to reconfigure the xserver to work with the new video hardware. and make sure the hard drive stays within the boot paramiters in your /boot/grub/menu.lst or you won't be able to boot. your bound to run into some problems that you'll have to work with.

---

### Post by Screwworkn on 2006-02-05
Thanks for the reply.  This is for a POS system and don't need any intensive graphics.  They will not be going into gnome until I need to get into it for something.  The biggest change between systems would be the type of network card.

Chris

---

### Post by az on 2006-02-05
Most hardware like network cards, cound cards and usb stuff is autodetected at boot time.  Things like your graphics card have a configuration that you need to redo if you change your video card.

What may be a problem is if you change the place of your hard drive.  Your mountpoints are determined by your /etc/fstab.  If your ftsab thinks your / directory is mounted on /dev/hdb (the slave of the first ide channel) and you actually put it on the master of the first ide channel, when you boot, your system will not be able to find itself.  Likewise, yout bootloader (grub) will not know where your kernel and system is.

Make sure that /boot/grub/menu.list and /etc/fstab are aware of any changes and you are good to go.

---

