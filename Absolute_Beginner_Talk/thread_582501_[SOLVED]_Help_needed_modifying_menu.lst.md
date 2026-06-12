---
title: "[SOLVED] Help needed modifying menu.lst"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by neu_ser on 2007-10-19
Hi, I have installed Kubuntu 7.04 on a system already booting vista and xp.
I did not specify where to write the bootloader during the install and (i think) grub overwrote the vista bootloader on my main raid partition.
Luckily (some would say) I have managed to restore the bootloader and all is well with the windows OS.

I need to now modify menu.lst and get Kubuntu booting.
Currently the important part looks something like this:

```
title=Kunbuntu Linux 7.04 <- not sure of the kernel but I guess it doesn't really matter
root (hd1,2)  <- educated guess, how would I find that out in linux?
kernel /kernel 2.6.10-5-386 <- suprisingly difficult to find out and I guess this does matter?
root=/dev/hda3 <- again, no idea
```

If I needed to I could possibly boot into Kubuntu via the live cd but have not as of yet.

After the bootloader incident I'm done just winging it. :)

sorry, I should have mentioned I am using EasyBCD and the menu.lst is on the windows partition.

Any help is much appreciated.

---

### Post by bodhi.zazen on 2007-10-19
Well, I am not following ...

menu.lst is used by GURB, the Linux boot loader ???

---

### Post by neu_ser on 2007-10-19
> **bodhi.zazen said:**
> Well, I am not following ...

menu.lst is used by GURB, the Linux boot loader ???

sorry, I am not 100% sure myself but I am using [EasyBCD]("http://neosmart.net/dl.php?id=1") and vista's bootloader which I think basically launches GRUB or atleast a version of it.

Currently I have a menu.lst file I need to modify inorder to boot Kubuntu.

---

### Post by bodhi.zazen on 2007-10-20
oic ...

easiest way is to copy the file from kubuntu ...

The general format is :

Title Kubuntu # can be anything
root (hdx,y)
kernel /boot/vmlinux-xyz root=/dev/sdxy ro quiet splash
initrd /boot/initrd-xyz

See if these links help at all :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Best Guide: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Supergrub : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by neu_ser on 2007-10-20
> **bodhi.zazen said:**
> oic ...

easiest way is to copy the file from kubuntu ...

The general format is :

Title Kubuntu # can be anything
root (hdx,y)
kernel /boot/vmlinux-xyz root=/dev/sdxy ro quiet splash
initrd /boot/initrd-xyz

See if these links help at all :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Best Guide: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Supergrub : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Thanks for the links, I appreciate the time taken to help me. 
I apologise if I seem like one of the crowd who doesn't read faqs or search before posting but really I do. I'm possibly just struggling to grasp this concept as I've been looking at it on and off for the last day or so.

I'll have to grab some sleep soon, but if possible could you explain the last 2 entries you posted?

---

### Post by bodhi.zazen on 2007-10-20
> **neu_ser said:**
> Thanks for the links, I appreciate the time taken to help me. 
I apologise if I seem like one of the crowd who doesn't read faqs or search before posting but really I do. I'm possibly just struggling to grasp this concept as I've been looking at it on and off for the last day or so.

I'll have to grab some sleep soon, but if possible could you explain the last 2 entries you posted?

LOL, no need to apologize at all. Most people feel grub is not very user friendly.

the first of the two links is the best guide I know, for you it will explain how to configure grub, I hope. I know it is long, just post with any specific questions and we will help.

The second link is for supergrub. supergrub may also be a helpful utility to boot Kubuntu without having to configure the windows boot loader.

---

### Post by neu_ser on 2007-10-22
Incase anyone is searching for a similar problem, the necessary code I needed to add was:
```
#Kubuntu
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic ro root=/dev/hdb2
initrd /boot/initrd.img-2.6.17-10-generic
```

Now I have another problem before I have even begun, it will not accept my login details.

Is there a default account that Kubuntu creates I can use ?

edit: Sorted, user name was lowercase :oops:

---

