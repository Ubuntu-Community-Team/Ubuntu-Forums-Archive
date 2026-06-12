---
title: "Ubuntu on Xserve  - can it be done?"
date: 2009-04-07
forum: Apple Hardware Users
---

### Post by BingoBilly on 2009-04-07
Can it be done?



well, I have read and searched but no luck.

Installed refit and it sees the Ubuntu install disk.... but alas, no luck past that.

.... someone mentioned using the refit bless with some success( but of course no explanation  : (

Would appreciate  any info.

Thanks!

---

### Post by cyberdork33 on 2009-04-07
yes, it can be done.

When you try to boot the CD from rEFIt, happens? what do you see?

---

### Post by BingoBilly on 2009-04-07
Thank you very much for the quick reply.

When it boots, holding down the option key, refit comes up and sees the mac os boot volume and the ubuntu live install cd lasted iso (stable)- penguin and all.

I click on the penguin and it acts like it is going to boot.. but quickly comes up with an error- roughly "legacy os could not be loaded- please update rom."

---

### Post by cyberdork33 on 2009-04-07
> **BingoBilly said:**
> Thank you very much for the quick reply.

When it boots, holding down the option key, refit comes up and sees the mac os boot volume and the ubuntu live install cd lasted iso (stable)- penguin and all.

I click on the penguin and it acts like it is going to boot.. but quickly comes up with an error- roughly "legacy os could not be loaded- please update rom."
well do you have all the firmware updates?

Holding Option should bring up the Apple boot chooser, not rEFIt. rEFIt should come up without holding option.

---

### Post by pxwpxw on 2009-04-07
AFAIK Xserve does not have the Apple bios emulation as used by refit for booting legacy stuff, and may not be directly  bootable from a  ubuntu install CD. Reports from users say it needs the efi boot method.

example -
[http://ubuntuforums.org/showpost.php?p=6823480&postcount=333](http://ubuntuforums.org/showpost.php?p=6823480&postcount=333)

I assume that this means you would run the ubuntu install CD by loading the install kernel using grub.efi on the OSX partition, but I have not seen any actual details of how they did it. Also may depend on the Xserve version.

A test version of grub.efi at post #523 could be tried. (There are some changes under discussion on grub-devel before it gets formalized on SVN trunk)
[http://ubuntuforums.org/showpost.php?p=6966036&postcount=523](http://ubuntuforums.org/showpost.php?p=6966036&postcount=523)

---

### Post by pxwpxw on 2009-04-08
Checked on an IMAC81, grub64.efi booting ubuntu904 altenate install CD, both i386 and amd64, both installers boot ok using this grub.cfg with grub.efi in the OSX partition root top level.
```

# grub.cfg 20090408 pxw
# comment lines are ignored

timeout=20
default=0

set F1=ctrl-x
set color_normal=yellow/blue

# OSX may need a different path for Xserve
menuentry "OSX" {
	search --set /usr/standalone/i386/boot.efi
	chainloader /usr/standalone/i386/boot.efi
}

menuentry "ubuntu alternate installer" {
	fakebios
	search --set /install/vmlinuz
	linux /install/vmlinuz video=efiifb noefi
	initrd /install/initrd.gz
}
# the 'noefi' option is needed for 2.6.28 amd64.
 
menuentry "REBOOT" {
	reboot
}

```

---

### Post by BingoBilly on 2009-04-10
when you say you tried this on an IMAC81, are you sayingthe 904 boot cd booted w/o any other software?

Also,  my experience has been that all the intel macs (except xserve) boot ubuntu 8.04 fine too...... it is just the server that will not boot ubuntu anyting.

Also,  in the post listing code ( see below) are you implying that the mentioned code needs to be on be added to the 9.04 boot cd somehow?

Can you please elaborate? a step by step of how to get ubuntu to boot and install on the Xserver,    I would think,  would form a really good FAQ or WIKI.

Many thanks

Bingo!

---

### Post by pxwpxw on 2009-04-10
> **BingoBilly said:**
> when you say you tried this on an IMAC81, are you sayingthe 904 boot cd booted w/o any other software?

Also,  my experience has been that all the intel macs (except xserve) boot ubuntu 8.04 fine too...... it is just the server that will not boot ubuntu anyting.

Also,  in the post listing code ( see below) are you implying that the mentioned code needs to be on be added to the 9.04 boot cd somehow?

Can you please elaborate? a step by step of how to get ubuntu to boot and install on the Xserver,    I would think,  would form a really good FAQ or WIKI.

Many thanks

Bingo!

Xserve 1,1 and 1,2 will boot linux using grub.efi, that includes installer cd kernels. 
If you have refit installed it will find grub.efi, if not you will need to bless grub.efi using OSX.

Please see the main grub.efi thread for details, goto post #585 and some previous Xserve tests, mentiioned above I think.

grub2 EFI boot loader internal/external booting
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)


We have just checked out for Xserve and user D4T just confirmed grub.efi booting 32 and 64bit linux.
[http://ubuntuforums.org/showpost.php?p=7042070&postcount=585](http://ubuntuforums.org/showpost.php?p=7042070&postcount=585)

---

### Post by rudyg13 on 2009-04-23
I don't mean this to be a TLDR request, but I started reading through all 60+ pages of that thread and got very lost.  Is it possible to get a step by step on how to shoe horn ubuntu onto an 1,1 xserve?  Thanks in advance.

---

### Post by pxwpxw on 2009-04-24
> **rudyg13 said:**
> I don't mean this to be a TLDR request, but I started reading through all 60+ pages of that thread and got very lost.  Is it possible to get a step by step on how to shoe horn ubuntu onto an 1,1 xserve?  Thanks in advance.

Start here
   [https://help.ubuntu.com/community/Xserve2-1](https://help.ubuntu.com/community/Xserve2-1)

and you can help me get the remaining information needed to complete the wiki for Xserve1,1.

That page covers intel Xserve generic, details only differ in choice of grub64.efi or grub32.efi, and all should be covered by grub2 rev 2121 except for current  update to fix grub64 memory bug with 4GB RAM in Xserve2,1.

I think Xserve 1,1 uses grub32.efi, easy to check with rEFIt 'About refit'
 
Its best to read the first and last posts in the 60 page grub efi thread, its is mainly filled with debugging or tests.

Will you compiles grub efi, or do I need to post rev 2121 binaries?

---

### Post by bopher on 2010-02-09
Hello Sir pxwpxw
 

 Good Day.
 

 I am using Xserve G5
 

 What I am doing now is,booting the Xserve with Linux in Fedora 11 installation CD (not a LiveCD) permanently.
 My procedures:
 1) I installed the refit
 2) modified the grub.cfg  
     yes,  i used the nomodeset.


0ne of my reference:

[http://www.4elements.com/blog/comments/install_fedora_on_xserve_part_three/P20/#c_65](http://www.4elements.com/blog/comments/install_fedora_on_xserve_part_three/P20/#c_65)

 What confuse me is that, it detects the hardware and then load the driver but it does not proceeds to the Anaconda graphics " Xstartup Failed" that was the error ,still it proceeded to a text base installations.
 

 ->NTP
 ->Language/country
 ->password  
 ->and the partitions(I choose to wipe out the entire disk)
 ->..and it continued the installations process
 g++  
 ..SELinux..
 etc
 --> Booting
 

 

 ==COMPLET INSTALLATIONS================
 You have installed successfully Please reboot(to be brief)
 =================================
 

  But after booting the Xserve ..just appear a white screen and a mouse
 pointer -that was it.,.       
 

 I am stuck now , my appreciation to those who could give a help
 

 

 ===Grub Configurations=============================
 # grub.cfg pxw 20090316
 

 timeout=20
 default=0
 

 set F1=ctrl-x
 set F2=ctrl-c
 set color_normal=yellow/blue
 

 menuentry "0-testfakebios and Loading Kernel" {
 # for debugging set debug=efi
    hexdump -s 0xc0000 (mem)
    fakebios
    hexdump -s 0xc0000 (mem)
 # deliberate error to get wait for key
         xxx
    fakebios
    root=cd0
    linux  /isolinux/vmlinuz
    root=CDLABEL=Fedora-11-x86_64 ro  rhgb single acpi=force irqpoll video=efifb nomodeset
    initrd /isolinux/initrd.img
 }
 

 

 

 # Testing Linux-MAC booting
 menuentry "1-FEDORA 11 over LEOPARD" {
  fakebios
  root=cd0
  splashimage=/EFI/BOOT/splash.xpm.gz
  linux /isolinux/vmlinuz  root=CDLABEL=Fedora-11-x86_64 ro rhgb single acpi=force irqpoll video=efifb nomodeset
  initrd /isolinux/initrd.img
 

 }
 

 # Testing Linux-MAC booting
 #menuentry "Fedora-11-x86_64-Live CD boot v2" {
 #       fakebios
 #       root=cd0
 #       linux /isolinux/vmlinuz0
 #         rootoCDLABEL=Fedora-11-x86_64
 #         rootfstype=auto ro liveimg  rhgb single acpi=force irqpoll video=efifb nomodeset
 #       initrd /isolinux/initrd0.img
 #}
 

 menuentry "REBOOT" {
         reboot
 }
 ===========================================
 

 

 Thanks in advance
 

 Christopher

---

### Post by linuxopjemac on 2010-02-10
I might be mistaken, but you have a PowerPC XServe, right? Shouldn't you be using a PowerPC based instalallation? I think your bootlaoder should be yaboot...

but you got into the installer, so I guess you are using an Intel based XServe?

---

### Post by bopher on 2010-02-11
Yes Sir ,

Actually I have both Intel and PPC xserve,soory; but that one mentioned
is intel.

Do you have Sie and idea how it cane be done?

> **linuxopjemac said:**
> I might be mistaken, but you have a PowerPC XServe, right? Shouldn't you be using a PowerPC based instalallation? I think your bootlaoder should be yaboot...

but you got into the installer, so I guess you are using an Intel based XServe?


Thanks

---

