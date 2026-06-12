---
title: "fdisk to install xp and then install ubuntu dual-boot."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by shillizzle on 2008-02-11
I have an acer 5100 laptop that came with vista loaded on it, after months of frustrations and hassles I began looking into linux/ubuntu, I made the decision that I wanted ubuntu to my my main choice for an os. After using a livecd to install, i admit that I was quite foolish in the fact that I was not clear on the install properties. I now have a fully working (beautiful_ os) Ubuntu. but I am having issues with getting java, my integrated webcam and a few other issues, I have researched how to do a proper install with xp installed first. I dont know how to delete ubuntu and get ready for the xp install, I have read a bit about -fdisk, but am not sure if my machine will be rendered useless before I can even attempt an xp install, not sure if i have to partition before, but i think its done in the xp install,and without an os(after deleting ubuntu) will the setup.exe run from the dvdrive? I was hoping that someone might guide me in the right directions to figure out how to do this, This time i am not going to rush into anything. btw i have backed up any and all files that want to keep, pics, documents and such. ive done soo much searching, but i feel like this is a needle in a haystack thing. thanks in advance for any  help i can get.
*cheers*

---

### Post by Presto123 on 2008-02-11
Your Windows disk will automatically get rid of your Ubuntu partition. Since you want dual boot, you are doing the right way of installing Windoze first, then Ubu. You don't have to worry about deleting the Ubu partition.

I just hope you have any wanted files backed up...

As for the Grub loader, it automatically sets up whatever you installed last as the first choice, so this type of setup will be fairly painless.

Windows disks don't really use .exe's until later on when you actually HAVE an NTFS (Windows) partition and uses an .ISO file (Auto-loading Image file) to begin installation. You shouldn't have any problems using the CD drive as it is already set up in the BIOS. 

Have you ever used the BIOS before?

---

### Post by dstew on 2008-02-11
If you were able to install Ubuntu from the DVD/CD drive, you should be able to install Windows from it also.

I recommend partitioning using gparted, which is a graphical partitioner, rather than fdisk, which is text-based. You can probably run gparted from the Live CD. You cannot partition easily from a hard-disk Ubuntu system, because it won't let you change the partitions if any of them are mounted (in use).

---

### Post by shillizzle on 2008-02-11
I have the bios loading the drive first, but when i reboot i can hear and see the drive being accessed but it still boots into ubuntu. is there a bios that i have to set inside ubuntu?? not sure if more info is necessary from my side of the fence. I know that the .iso of my install disk is good, i can start it in wine, but i get an error when trying to start the install from the wine application, and i understand that i have to start the install from the boot drive.

---

### Post by oedha on 2008-02-11
it means you win cd is not in good shape :)
or have you press any key after you boot he cd up.....because you need to press any key to boot into win installation

---

### Post by dstew on 2008-02-11
> i can hear and see the drive being accessed but it still boots into ubuntuAre you referring to the same Live CD that you installed with?

---

### Post by Presto123 on 2008-02-11
Yes, if you wish to install Windows to your hard drive, you would need to boot from the very beginning. It will wipe out everything in your computer as far as files and OS's go and you will definitely be starting fresh.

The BIOS is the settings that are hardwired into your motherboard and will not be found in any of the OS's. It's just the basics to make sure that when you get your computer and you have NO OS or need to mess with something, you can do it without any form of an OS.

What you will need to do is when you first start up the computer to check the screen that first pops up. It will list (most likely) two options and one is probably something like "Hit Delete (Or possibly another key) to Change Settings" or "Hit Delete to Enter Bios". Mine also has an option to select bootup drive, and if you use this, it will be an even easier way to boot the disk.

Otherwise, in the BIOS, you will have a menu of all kinds of stuff and one should say something like "Boot Priority". Don't ever delete any of this stuff listed, but if you follow the menus, you can move the disk up on the list. You make the CD to boot first.

If you have any issues with this feature, post back and don't touch anything.

**Edit**I think I'm behind, but this could still be useful. (??) **

---

### Post by mikewhatever on 2008-02-11
> **shillizzle said:**
> I have the bios loading the drive first, but when i reboot i can hear and see the drive being accessed but it still boots into ubuntu. is there a bios that i have to set inside ubuntu?? not sure if more info is necessary from my side of the fence. I know that the .iso of my install disk is good, i can start it in wine, but i get an error when trying to start the install from the wine application, and i understand that i have to start the install from the boot drive.

Here are two guides on Windows XP installation:
[http://theeldergeek.com/xp_home_install_-_graphic.htm](http://theeldergeek.com/xp_home_install_-_graphic.htm)
[http://theeldergeek.com/xp_pro_install_-_graphic.htm](http://theeldergeek.com/xp_pro_install_-_graphic.htm)

As for fdisk, the program needs DOS to work, so if you don't have it, no, setup.exe would not run from a DVD.

---

### Post by shillizzle on 2008-02-12
thanks for all the help :) i had my drive booting first, but i needed to have the boot agent first, everything went well (or at least i thought) untill it came time to boot my fresh xp install and i got the blue screen of death, i had a older xp light disk in a drawer from my old pc and when it took 2 or more hours to install and then all the crap that i had to go through, i just realized how much i have fallen in love with ubuntu. for the very few windows programs that i want to run, I will give the virtualbox a go, anyone know any good links to some informative guides to virtualbox or what is the name of the package that I would look for in the repositories.
Thanks again for the help guys, this forum is the best I have seen for getting prompt advice:guitar:

---

### Post by antisocialist on 2008-02-12
> **shillizzle said:**
> but I am having issues with getting java,and a few other issues,to install java flash mp3 mp4 and other proprietary formats merely go to applications>add/remove and then search for "ubuntu restricted extras"
tick the box and hit apply and As far as I know it will do the rest for you because ubuntu is cool like that ;)
cheers

---

