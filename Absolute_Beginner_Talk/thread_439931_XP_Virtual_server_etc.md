---
title: "XP Virtual server etc"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Steve H on 2007-05-11
I´ve got my old XP installation, which I want to mount using Qemu or some such. I don´t really want to loose my data, or have to install another copy. I have a couple of programs that I use in XP which don´t work using WINE, so I need to keep rebooting and using the prog then rebooting again to get back to Ubuntu. Kind of annoying!!

So does anyone know how I can use Qemu or something to mount and use my XP partition??

Can I create an image from my old XP or can I mount it direct??

Any help would be appreciated.

:)

---

### Post by Jazztux on 2007-05-11
Hi,
You can try to use it directly, it should work. ;)

---

### Post by Steve H on 2007-05-11
Thanks for your reply, I couldn´t get Qemu to work so I have now turned to VMware (VMplayer) via Synaptic but I am getting a error with the ¨virtual¨ grub:

```
GRUB Loading stage1.5

GRUB loading, please wait...
Error 21
```

Still looking for an answer. I did notice someone say:

> My dual-boot system consists of two hard disks with HD(0) running Windows and HD(1) running Linux. For GRUB is installed within the Linux system, the bootloader searches for the second disk HD(1) at boot time.
After I had mounted both disks in the virtual machine exactly the way as in reality, the GRUB boot menu appears when starting the virtual machine. Choosing 'Linux' starts the OS the same way as when booting physically. 

But I´m not sure what is meant by ¨Mounted both disks in the virtual machine¨....

Any ideas??

:)

---

### Post by Jazztux on 2007-05-11
Well, I can suggest two ways to try get it working:
1. You can try to "skip" the bootloader trying to start directly the win partition
2. You can make a "virtual" mini HD with the bootloader installed configured properly to boot you system.

I must say I never used VMware, so now I want to install it and try the same thing you're trying to do. ;)

---

### Post by Steve H on 2007-05-11
> **Jazztux said:**
> Well, I can suggest two ways to try get it working:
1. You can try to "skip" the bootloader trying to start directly the win partition
2. You can make a "virtual" mini HD with the bootloader installed configured properly to boot you system.

How would I ¨skip the bootloader¨? I have tried rewriting the virtual MBR in order to try and get it to just boot from the windows partition, but that didn´t work. I have followed [_this thread_]("http://ubuntuforums.org/showthread.php?t=380699&highlight=create+vmx"), but I´m still not finding any answers.......

:)

---

### Post by Steve H on 2007-05-14
Thanks for the help but I have given up with my old windows installation. It was flakey at the best of times and so I ditched it.

I have now setup a 10 gig partition, which I used to install a fresh XP, through VMPlayer. It now boots and works fine. I did try everything to get my old install to work, but cut my losses on Saturday, I backed up all the stuff I thought I might need (or just moved it over to my Ubuntu install anyway). I only need a native XP for 2 programs (Stackz list editor & Nokia PC suite), so I was happy to free up 68gig of useless space which the XP partition was hogging. I am now trying to get the VM-XP to share files through a SAMBA share, but for some reason it "has network difficulties" when trying to authenticate itself to SAMBA. ho-hum.

Thanks to everyone for your help anyway.

:)

---

