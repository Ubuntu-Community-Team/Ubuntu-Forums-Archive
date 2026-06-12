---
title: "Installing Windows Over Ubuntu"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-21
Hi there, purely because of the lack of ease with getting games to work in Ubuntu I am switching to using Windows as well. Only thing is last time I installed windows over Linux it rewrote the bootloader thus making my linux installs unaccessible and erasing GRUB. Is there any way to make sure that they are both bootable? Detailed instructions would be greatly appreciated!

Thanks very much

---

### Post by Jussi Kukkonen on 2006-11-21
Well, as far as I know, there's nothing you can do: Windows always overwrites the bootloader. I view this as a prime example of Microsoft "interoperability" -- I don't know of any other modern Operating system that would do this.

You'll need to use a boot CD: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by rlozano on 2006-11-21
best thing is for you to install Windows first before ubuntu. if in case you have ubuntu already in your machine and windows will come in second in installation sequence, windows will overwrite the MBR. 

your work around there is to install GRUB manually in the MBR and define in the Grub Menu the OS that you need to boot. 

for further Grub information, just search the forum and you will see tons of GRUB discussion.

---

### Post by steve.horsley on 2006-11-21
If you manage to install windows and leave your Ubuntu partitions intact, you can use the rescue mode on the alternate installer, jump to the Ubuntu partition and run the command:
**grub-install /dev/hda**
(or /dev/sda if it's a SATA disk), and this will replace GRUB.

---

### Post by John E on 2006-11-21
> **Jussi Kukkonen said:**
> Well, as far as I know, there's nothing you can do: Windows always overwrites the bootloader. I view this as a prime example of Microsoft "interoperability" -- I don't know of any other modern Operating system that would do this.Well that's a perfectly reasonable criticism - until you get to your conclusion! The same criticism is true of most boot loaders - including GRUB. Try removing Linux from a multi-boot system and see if GRUB will still let you boot up the other OS's. It wouldn't on my system. :(

---

### Post by maximouse on 2006-11-21
> **John E said:**
> Try removing Linux from a multi-boot system and see if GRUB will still let you boot up the other OS's. It wouldn't on my system. :(

I guess that depends a bit on how you remove linux. As far as I know GRUB will work as long as it is still properly configured. If your /boot partition is intact, it should boot other OS's. Even without the linux install.
If you remove /boot (a big part of GRUB), you should remove GRUB from the MBR as well.

In reply to the original poster, I think the "Super Grub Disk" might solve your problems. [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by pingvin on 2006-11-21
GRUB is inter-operable from the perspective that it takes other OSes into account. When you install GRUB, it looks for other OSes and populates its list accordingly, thus making it very inter-operable. Removing an OS it a different kettle of fish, however NTloader fails on both accounts :-)

Mike

---

