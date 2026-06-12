---
title: "Boot into Command Line"
date: 2007-11-26
forum: Apple PPC Users
---

### Post by Black Mage on 2007-11-26
I just installed Ubuntu 7.10 ppc version on my emac. Now the screen goes blank on start up and I need to edit some xorg setting but I can't get to it. So how can I boot to the command line the in the yahboot or grub bootloader?

---

### Post by akiratheoni on 2007-11-26
There is a recovery mode in GRUB when you boot up that you can select to go into a command line only mode -- be careful, though, you're logged in as root there.

---

### Post by Nano Geek on 2007-11-26
Select Ubuntu*blah*blah*blah*(recovery mode) from the grub menu and you'll be taken to the command-line.

P.S. This should have been put into one of the support forums.

---

### Post by Black Mage on 2007-11-26
I can't even get there. Once I choose the boot, it says loading grub, and then the screen goes blank.

And I only have two options in the boot prompt when I press tab, Linux and old, and old doesn't work.

---

### Post by Nano Geek on 2007-11-26
> **Black Mage said:**
> I can't even get there. Once I choose the boot, it says loading grub, and then the screen goes blank.That's strange. It sounds more like a problem with your computer than with Ubuntu. 
Does a live-cd work?

---

### Post by Black Mage on 2007-11-26
I installed using an alternative. but that works.

---

### Post by init1 on 2007-11-26
> **Black Mage said:**
> I installed using an alternative. but that works.
Boot with a Linux live CD and reinstall GRUB. The code is as follows:
```

grub-install  --root-directory=DIR /dev/xxx

```
xxx is your hard drive device. If you don't know it, do a 
> 
fdisk -l

to see some possible devices. The root directory should be the "/" of the partition Ubuntu is installed to. So if your hard drive is "/dev/hda" and the Ubuntu partition is mounted to "/mnt" then 
```

grub-install  --root-directory=/mnt /dev/hda

```
Do not run this command unless this applies to your system. Your hard drive may be another device such as "/dev/sda"

---

### Post by Nano Geek on 2007-11-26
That's strange. So even booting into recovery mode the screen turns dark?

If that's the case then a reinstall would probably be the surest way of fixing it. If you don't want to do that then I could try to find some more information for fixing your problem.

---

### Post by Black Mage on 2007-11-26
Well, its not grub its using, its Yahboot. And its not the reinstall, I just need to change the setting mentioned here.

[http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/](http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/)

I can do rescue-powerpc from the altnerative CD, but when i run the shell and use vi, , I can't edit the files correctly even using the sudo. The keyboard doesn't work correclty. Is there another editor? And I tried nano but that doesn't work.

---

### Post by Nano Geek on 2007-11-26
> **Black Mage said:**
> Well, its not grub its using, its Yahboot. And its not the reinstall, I just need to change the setting mentioned here.

[http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/](http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/)

I can do rescue-powerpc from the altnerative CD, but when i run the shell and use vi, , I can't edit the files correctly even using the sudo. The keyboard doesn't work correclty. Is there another editor? And I tried nano but that doesn't work.Try this:

[SIZE=4]**Repairing Your Broken Ubuntu Install**[/SIZE]
[SIZE=1]Brought to you by [PriceChild]("http://ubuntuforums.org/member.php?u=43712")
Edited by myself
[/SIZE] 
If you can, it is preferable to just boot using a backup kernel or into recovery mode and update from there. If you can't:
[LIST]
[*] Boot up a live cd, or separate Linux install
[*] Mount your Ubuntu drive somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.) 	Code:
 	sudo mkdir /media/ubuntu
sudo mount /dev/**** /media/ubuntu 
[*] chroot into your Hardy drive
 	Code:
 	sudo chroot /media/ubuntu su 
[*]Run commands to fix your problem[/LIST][LIST]
[*]Ctrl+d or type "exit" to exit the chroot, then reboot the computer and you should be able to get back into Ubuntu.[/LIST]

---

### Post by pxwpxw on 2007-11-27
> **Black Mage said:**
> I just installed Ubuntu 7.10 ppc version on my emac. Now the screen goes blank on start up and I need to edit some xorg setting but I can't get to it. So how can I boot to the command line the in the yahboot or grub bootloader?

From the yaboot boot menu
```

boot: Linux single

```

boots into your installed system console as root, sudo not required.

---

### Post by Black Mage on 2007-11-27
The screen still goes blank. So I'm either going try and use the LiveCD or install 7.04.

---

