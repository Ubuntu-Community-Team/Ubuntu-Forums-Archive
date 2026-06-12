---
title: "Beige G3 Install goes fine but how to boot into Ubuntu After???"
date: 2004-11-11
forum: Apple PPC Users
---

### Post by kingnubian on 2004-11-11
Have a beige G3 mac and got Ubuntu installed using guides such as [http://animefreak.ath.cx:9000/index.php/2004/08/06/installation-of-debian-linux-on-a-powermac-g3-beige/](http://animefreak.ath.cx:9000/index.php/2004/08/06/installation-of-debian-linux-on-a-powermac-g3-beige/)

According to how the drive is partitioned Ubuntu is on hda8.

The problem is now how to boot into the Ubuntu system. Using the kernel and initrd from the PPC folder with BootX, the same used to get the install going, is strange as it  will come to the install options page even if the cd is not in. putting in the kernel options in BootX as "root=/dev/hda8 noinitrd" doesn't work.

I am not a Mac person as I'm posting this for a friend desperate to getting this working. 

Can someone please give him, through me, some insight as to what can be done??? :-?

---

### Post by kingnubian on 2004-11-11
[QUOTE=kingnubian]Have a beige G3 mac and got Ubuntu installed using guides such as [http://animefreak.ath.cx:9000/index.php/2004/08/06/installation-of-debian-linux-on-a-powermac-g3-beige/](http://animefreak.ath.cx:9000/index.php/2004/08/06/installation-of-debian-linux-on-a-powermac-g3-beige/)

According to how the drive is partitioned Ubuntu is on hda8.

The problem is now how to boot into the Ubuntu system. Using the kernel and initrd from the PPC folder with BootX, the same used to get the install going, is strange as it  will come to the install options page even if the cd is not in. putting in the kernel options in BootX as "root=/dev/hda8 noinitrd" doesn't work.

I am NOT a Mac person as I'm posting this for a friend desperate to getting this working. 

Can someone please give him, through me, some insight as to what can be done??? :-?[/QUOTE]


I should add that the system installs fine but when it gets to that point that it asks to reboot he can't get back into Ubuntu to complete the install and consequently can't use his newly installed Ubuntu linux system.

---

### Post by kanem on 2004-11-11
Every linux distro that I've put on my oldworld mac required that the actual kernal that you'll be using, the ubuntu kernel in this case, be put on the mac partition in /system folder/Linux Kernels. I don't think bootx can access the linux partition. The ubuntu installation probably just put this kernel in the linux partition where it usually goes. In bootx you select the ubuntu kernel that you've placed in the Linux Kernels folder.

If this works could you post back to say if the rest of the installation and everything else works like apt-update and such? I really want to try this with my oldworld, but don't want to wipe my current installation or buy a new hard drive 'till I'm sure it works. thanks

EDIT: it just occured to me that the first part of the installation doesn't give you a chance to move the kernel over to the mac side. And you won't be able to get to it from the mac side. One way is to have another linux installation with which you can access both the mac side and the newly installed ubuntu partition. I have a small (~2GB) yellow dog linux installation for these kinds of things. Or if you can get your oldworld to boot off another live linux cd (like gentoo for ppc) that would allow you to move the kernel to the mac side. I never got my mac to boot off a live cd.


[QUOTE=kingnubian]I should add that the system installs fine but when it gets to that point that it asks to reboot he can't get back into Ubuntu to complete the install and consequently can't use his newly installed Ubuntu linux system.[/QUOTE]

---

### Post by Somatik on 2004-11-11
check this thread, i got the same problem :s

[http://www.ubuntuforums.org/showthread.php?t=747&highlight=g3](http://www.ubuntuforums.org/showthread.php?t=747&highlight=g3)

---

### Post by kingnubian on 2004-11-11
[QUOTE=Somatik]check this thread, i got the same problem :s

[http://www.ubuntuforums.org/showthread.php?t=747&highlight=g3](http://www.ubuntuforums.org/showthread.php?t=747&highlight=g3)[/QUOTE]


From what I can gather seems it is a bug in the initrd used not loading the proper driver for disc access soon enough. If so is a workable "Fixed" initrd file available???

---

### Post by kanem on 2004-11-13
I have Ubuntu fully installed on my oldworld G3 now.

The first part of the installation puts a new kernel and initrd image in the /boot folder on the Ubuntu partition. This kernel has to be put in the Linux Kernels folder on the mac. You can't use the same kernel as the one that was used for the first part of the installation. Same for the initrd image. The new one has to be copied from the /boot folder to somewhere on the mac (I just put mine on the mac desktop) so bootx can use it as a ramdisk image.

When it boots from this new kernel the second part of the installation starts.

---

### Post by kingnubian on 2004-11-14
[QUOTE=kanem]I have Ubuntu fully installed on my oldworld G3 now.

The first part of the installation puts a new kernel and initrd image in the /boot folder on the Ubuntu partition. This kernel has to be put in the Linux Kernels folder on the mac. You can't use the same kernel as the one that was used for the first part of the installation. Same for the initrd image. The new one has to be copied from the /boot folder to somewhere on the mac (I just put mine on the mac desktop) so bootx can use it as a ramdisk image.

When it boots from this new kernel the second part of the installation starts.[/QUOTE]


Now the question is if I can't get it to boot into Ubuntu and Mac OS 9.2 can't see the partition what are the steps for getting access to the Ubuntu partition, in my friends' case hda8, and copying over the necessary kernel and initrd file??

---

### Post by kanem on 2004-11-15
[QUOTE=kingnubian]Now the question is if I can't get it to boot into Ubuntu and Mac OS 9.2 can't see the partition what are the steps for getting access to the Ubuntu partition, in my friends' case hda8, and copying over the necessary kernel and initrd file??[/QUOTE]

yup, thats the hard part. 

What should be the quick and easy way would be to use a live linux cd. These are rare for ppc, the only one I know of is Gentoo's. None of the installation would have to be done, just booting from it should be enough. Once booted into the live cd, make two directories and mount both the Ubuntu and Mac partitions to them and copy the kernal and initrd image over to the Mac side. 

Possible problems with this are that many people (including me) had a very diffifcult time trying to get oldworlds to boot from the Gentoo live cd. It's easy to do if it works (just uses bootx), it's just that it often didn't. That was with 2004.1. They just released 2004.3 which may have fixed this problem. It also might be the case that the live cd doesn't write to the Mac's filesystem (hfs), although it probably does.

The brute force method that definitely works is to have another linux installation already on another partition. This is what I had, so after the first part of the Ubuntu installation I just booted into my other linux distro, mounted the new Ubuntu partition and copied the files over. Installing another distro to get Ubuntu on may seem like alot of effort and wasted space, but I think it's worth it. I always have another small linux installation anyway in case I completly screw up the one I usually use. YellowDog 2.3 is relatively easy and quick to install and you could wipe it afterwards if you want. After 2.3 I think YellowDog starts to be less oldworld friendly.

So far Ubuntu is working great. I've already done a dist-upgrade, as well as other installed other packages. It even set up Alsa for whatever strange onboard soundcard this G3 has. And things run *alot* faster than on my YellowDog installation.

---

### Post by ktindle on 2004-11-19
I didn't use BootX, I used miBoot from Linux PPC 2000.

I got the install working with a beige G3 by dropping to a console (Ctrl-Option-F2) and using
pivot_root to get into the newly installed distro.  This gives you a version of mount that can
mount an HFS partition, and you use cp to get the kernel into Linux Kernels and the initrd into
the root of the HFS volume.  Then you have to go through the install again, after booting with a
Mac OS 9 CD to set boot.conf.  Do the pivot_root when the Ubuntu installer is prompting you
for a reboot.  The first "install" just generates the kernel image and initrd you need.

This isn't my idea- check the wikipage for a recent article on BootingOldWorldMacs.

---

### Post by kanem on 2004-11-19
Good the more ways the better. 

the howto wiki using the miboot option ([http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)) has a link which it says has the final kernel and initrd image, so thanks to the author one can just download them while still in the mac and place them in the appropriate place before the installation.

Also, towards the bottom of the wiki someone has told how they just used debian bootable floppies (instead of a live cd like I suggested a few posts ago) to copy the new kernel and image over to the mac.

---

### Post by heavyt on 2004-11-27
[QUOTE=kanem]Good the more ways the better. 

the howto wiki using the miboot option ([http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)) has a link which it says has the final kernel and initrd image, so thanks to the author one can just download them while still in the mac and place them in the appropriate place before the installation.

Also, towards the bottom of the wiki someone has told how they just used debian bootable floppies (instead of a live cd like I suggested a few posts ago) to copy the new kernel and image over to the mac.[/QUOTE]

I have a PoweCurve Mac clone with a g-3 chip and so far I am unable to boot into Ubuntu after the first stage install with bootX. I used a Gentoo live cd to chroot into Ubuntu and copied the vmlinux and the initrd image from /boot to my Mac partition. I then selected the vmlinux and the initrd image, that was copied to the Mac side, with bootX then launch bootX but it only got to the tux image but nothing else. Is there some settings that I should have in the bootX argument 
 section? Or could someone post a link to their vmlinux and initrd that I could try. I went to [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs) but it does not have any vmlinux in the tarball, thanks.

---

### Post by jdong on 2004-11-27
Not a mac user, but do the colors actually mean anything?

---

### Post by heavyt on 2004-11-28
How does that help me?

---

### Post by kanem on 2004-11-28
[QUOTE=heavyt]I have a PoweCurve Mac clone with a g-3 chip and so far I am unable to boot into Ubuntu after the first stage install with bootX. I used a Gentoo live cd to chroot into Ubuntu and copied the vmlinux and the initrd image from /boot to my Mac partition. I then selected the vmlinux and the initrd image, that was copied to the Mac side, with bootX then launch bootX but it only got to the tux image but nothing else. Is there some settings that I should have in the bootX argument 
 section? Or could someone post a link to their vmlinux and initrd that I could try. I went to [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs) but it does not have any vmlinux in the tarball, thanks.[/QUOTE]

in the kernal options line in bootx goes root=/dev/hda8. hda8 should change to whatenver partition you have as your ubuntu root partition. 

The vmlinux you got from your /boot partition: was the full name something like vmlinux-2.6-powerpc?

i'll put the images on a geocities website in a few days. the monitor for my ppc just fried and i can't do anything with it till i get a new one. i'll post again when they are available

---

### Post by heavyt on 2004-11-28
[QUOTE=kanem]in the kernal options line in bootx goes root=/dev/hda8. hda8 should change to whatenver partition you have as your ubuntu root partition. 

The vmlinux you got from your /boot partition: was the full name something like vmlinux-2.6-powerpc?

i'll put the images on a geocities website in a few days. the monitor for my ppc just fried and i can't do anything with it till i get a new one. i'll post again when they are available[/QUOTE]

No luck. I put root=/dev/sda2 in kernel arguments and used vmlinux-2.6.8.1-3-powerpc but it only gave me a black screen with tux in the upper left hand corner. After about 3 minutes my computer did an auto reboot into Mac OS.

---

### Post by cosmo on 2004-11-30
[QUOTE=heavyt]No luck. I put root=/dev/sda2 in kernel arguments and used vmlinux-2.6.8.1-3-powerpc but it only gave me a black screen with tux in the upper left hand corner. After about 3 minutes my computer did an auto reboot into Mac OS.[/QUOTE]


Well I installed Ubuntu on a beige G3 with a Sonnet G4 PCI Upgrade & ATI Radeon 7000 with not too much problems. What I missed in the beginning is that you have to choose with the 2.6.8 kernel always the initrd image under the options of Bootx. The root path goes into the kernel argument box. Maybe a video argument would help you to see what's going wrong. My ram disk size is set to 16384.

Just my 2 cents :)

---

