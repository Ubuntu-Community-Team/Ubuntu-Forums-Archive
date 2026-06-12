---
title: "Need install help, GRUB issue, DESPERATE!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by CUrza on 2008-02-19
Ok, here's the basics: I am a complete noob. I created two partitions, named C and D, for running Windows XP and Ubuntu. I installed and updated Windows as an NTFS system on C this morning. Then, I went to Ubuntu and used the partition editor to resize D into 20GB and 5GB swap space (just a guess, I read I only needed 2GB swap but I dunno...moving on). So, I go to install Ubuntu. I click "Manual" on the partitions screen. I choose my 2nd partition, the one called D. I make it a ext3 partition, and in the mount point form I type "/" just like it says. I then edit the 5GB partition to be swap space, and click next. I choose not to import my info from XP. I look at Advanced, and the box to install the boot loader is checked, and the place to install is listed as hd0. At 94%, the error "Executing 'grub-install' (hd0) failed. This is a fatal error." Then I tried to reinstall on hd1, thinking maybe that would do something different, but no. I know there is a thread on this but I am very new and I do not understand any of this. Could someone please help? Also it says my HD is a SCSI3, if that helps...thanks in advance

PS - the partition for Windows is /dev/sda1, and it has a boot flag on it...dunno what this means but maybe it will tell you all something. Alternatively, could I install Ubuntu first and then put Windows on in another partition created with GParted??

---

### Post by TeoBigusGeekus on 2008-02-19
I had exactly the same problem. It happens whenever you install Ubuntu without being connected to the internet (a bug?).
Get yourself a router and install winxp. From there, configure your router so that you can connect to the internet.
Reboot and try to install Ubuntu again. During installation, the setup will search for updated install files from the net and everything will go on smoothly.
I really hope I've helped you. Good luck!

---

### Post by criskat777 on 2008-02-19
do u see winjunk on the grub menu? do you even have a grub menu?

---

### Post by justleen on 2008-02-19
> **TeoBigusGeekus said:**
> I had exactly the same problem. It happens whenever you install Ubuntu without being connected to the internet (a bug?).
Get yourself a router and install winxp. From there, configure your router so that you can connect to the internet.
Reboot and try to install Ubuntu again. During installation, the setup will search for updated install files from the net and everything will go on smoothly.
I really hope I've helped you. Good luck!

..uhm this is not gonna be helpfull, but i installed  3 ubuntu desktops today, without network...

i dont know where the error is coming from, but wether you have a interconnetion or no, you can install just fine. (you DO get a msg telling you that no updates could be run without inet connection)

OP: did you try with the ption NOT to install grub?
that way it would skip the grub install.. you could then boot with the live cd, and add grub later?

bit of a hassle, but all i can think of right now

---

### Post by criskat777 on 2008-02-19
he does not give much info but he can use a super Grub disk that will help him edit grub

---

### Post by northern lights on 2008-02-19
> **CUrza said:**
> it has a boot flag on it...dunno what this means but maybe it will tell you all something

GRUB (& LILO, I think) ignore the bootflag. Dunno 'bout NTLDR.

> **CUrza said:**
> Alternatively, could I install Ubuntu first and then put Windows on in another partition created with GParted??

Theoretically you can, but Windows will overwrite the MBR upon installation and your old bootloader will be gone. Plus, even without Windows will Ubuntu install grub.

---

### Post by Berean on 2008-02-19
I would have to agree.  Get yourself a router (with LAN cable attached to PC) and then reinstall Ubuntu.  I've had a similar problem but started XP and then pressed Ctrl-Alt-Del and followed the instructions to install Ubuntu, readjusting the size of the partition as required.  Incidentally, prior to that I went into to XP and deleted the partition that had already been made by my initial install.  Everything then went smoothly.  If you have a problem with the GRUB loader only, reinstall it by selecting the relevant section when you put the CD in the drive and reboot WITHOUT installing the whole distro to your hard drive again.  Hope this adds to the previous thread.

---

### Post by CUrza on 2008-02-19
Don't I need to install GRUB to have a GRUB menu? I suppose I could just install without bootloader and boot from the CD, but I am unsure of how to add GRUB later.

---

### Post by Duck2006 on 2008-02-19
> **CUrza said:**
> Don't I need to install GRUB to have a GRUB menu? I suppose I could just install without bootloader and boot from the CD, but I am unsure of how to add GRUB later.

This will help with install grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by criskat777 on 2008-02-19
ok will take it slow. when you turn on your PC does it boot at all? if it does does it go to winjunk or does a black screen with options come up? not trying to be a @$H0! just trying to help

---

