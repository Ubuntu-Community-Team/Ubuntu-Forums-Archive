---
title: "how do i install several linux os's and have ubuntu as default?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by randum on 2007-03-14
I currently have Windows XP and Ubuntu Edgy installed, i want to install several more linux os's (Kubuntu, Mint Linux, Debian, and others) to see how they compare. I would like the default os to be ubuntu, but i know that when i install a new os it will take over the GRUB and make itself the default. How would I go about changing it back to Ubuntu afterwards? Also, how many OS's is it possible to install? Also, can i use the same swap space for all linux OS's? Thanks..

---

### Post by oilchangeguy on 2007-03-14
why not use vm ware? instead of clogging your hard drive with many operating systems. also microsoft has free virtualization software available. download that in your xp install and load your linux software there.

---

### Post by tommcd on 2007-03-14
When you install the other OSs you can either choose not to install grub, and then run <sudo update-grub> from from ubuntu which should add an entry for the new OS. Or you can add an entry for the new OS manually. Or you can install the new OSs grub to it's partition instead of the MBR and chainload the new OS from ubuntu's grub. If this sounds confusing, it can be. See Herman's grub page for the details:
 [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
All you need to know about grub. Specifically, see this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
Also, get a super grub disk and have it handy, just in case:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Hope this helps.
If all else fails you can reinstall grub using the live or alternate CD. Instuctions are on Herman's grub page.

---

### Post by randum on 2007-03-14
> **oilchangeguy said:**
> why not use vm ware? instead of clogging your hard drive with many operating systems. also microsoft has free virtualization software available. download that in your xp install and load your linux software there.

I want to put them on the hard drive, though. I have Ubuntu as my main OS, the only reason i have windows is because i have certain software i cant use with WINE and also i have a dell all in 1 printer which the Ubuntu doesn't have drivers for..

I am interested in figuring out how to run windows XP with VMWare under Ubuntu though.. Then the only reason to boot to WinXP is to use the Dell printer/scanner..

---

### Post by tech overloaded mom on 2007-03-14
I'm sure oilchangeguy's answer is better in the long run, but I ran across this yesterday:
If you edit the Grub menu and cut and paste so that the OS you want to be the default is at the top of the list that is what it will boot to. At the terminal type 
sudo gedit /boot/grub/menu.lst

---

### Post by randum on 2007-03-14
> **tommcd said:**
> When you install the other OSs you can either choose not to install grub, and then run <sudo update-grub> from from ubuntu which should add an entry for the new OS. Or you can add an entry for the new OS manually. Or you can install the new OSs grub to it's partition instead of the MBR and chainload the new OS from ubuntu's grub. If this sounds confusing, it can be. See Herman's grub page for the details:
 [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
All you need to know about grub. Specifically, see this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
Also, get a super grub disk and have it handy, just in case:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Hope this helps.
If all else fails you can reinstall grub using the live or alternate CD. Instuctions are on Herman's grub page.

I have a super GRUB disk, but when i installed windows and then ran the super GRUB disk to fix the MBR it screwed everything up and i was unable to load either. I ended up formatting everything and then installing XP first then Ubuntu....

---

### Post by tommcd on 2007-03-14
Did you try reinstalling grub from the live or alternate CD? In any case see Herman's grub page, it really has all the answers.

---

### Post by confused57 on 2007-03-14
> **randum said:**
> I have a super GRUB disk, but when i installed windows and then ran the super GRUB disk to fix the MBR it screwed everything up and i was unable to load either. I ended up formatting everything and then installing XP first then Ubuntu....
tommcd gave you some excellent advice and links to Herman's site.

What I do is, as was suggested, is install grub for the new distro to it's root partition...then add an entry to Ubuntu's menu.lst to boot it by chainloading:

title   New Distro
rootnoverify  (hdx,y)
chainloader  +1

If for some reason your new distro overwrites your mbr, you can restore Ubuntu's grub to the mbr and install the new distro's grub to it's root partition, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
I had this happen when I installed Sabayon, I just booted up the live cd:
```
sudo grub
find /boot/grub/stage1
root (hd0,1)  <---if this is Ubuntu's root partition
root (hdx,y)   <---new distro root partition
# then do this
root (hd0,1)
setup (hd0)
root (hdx,y)
setup (hdx,y)
quit
```

Add the entry to Ubuntu's grub to boot the new distro and you're good to go.

---

### Post by tommcd on 2007-03-14
Just be sure to add the entry for the new OS after the ### END DEBIAN AUTOMAGIC KERNELS LIST, where windows is, either above or below windows. This way ubuntu will always be the default OS to boot. When I installed zenwalk I did not install lilo (zenwalk uses lilo). I just added an entry for zen and it boots fine. I'm at work now, when I get home I'll post the exact entry for zenwalk from my grub list.

---

### Post by gnoel on 2007-03-14
Before I did any multi-OS fancy stuff, I'd buy another hard drive, format it to FAT32, and put all my documents and media files on it.  Any recent Linux distro as well as all Windoze can use FAT32, and you'll sleep better once you've got your vital data safe from your operating systems experiments.

Installing a second HD in a desktop is a piece of cake - you literally just plug it in.  Afterwords, you'll need to edit your Ubuntu /etc/fstab file (don't forget to make a backup first) to add the new mount points for the new data hard drive.  In the following example, I have one Win XP NTFS partition on my OS drive (hda1) mounted as /media/windows, and a FAT32 partition on my data disk (hdb5) mounted as /media/data1:

/dev/hda1 /media/windows ntfs umask=0222 0 0
/dev/hdb5 /media/data1 vfat umask=0000 0 0

This is all well-documented in the Ubuntu user guide.

---

### Post by SactoBob on 2007-03-14
If you have the memory and disc space and a Windows license, VMWare Player is the quick,  easy and best solution.

Since your booting Win, go to VMware website and download and install the Win version of VMWare Player - free and very fast and easy.

Then go to [www.easyvmx.com](www.easyvmx.com) and take a few minutes to create a virtual machine.  Specify XP as host and Linux as guest OS.  Assign it a reasonable amount of memory and disk space.  Download the zip and unzip it to a Win directory.  Do it in under 5 minutes.

Start VMWare Player and point it to your new virtual machine with Unbuntu in the CD drawer and start installing.  You can run as many distros as you like if you have the disk space, and can even run them at the same time if you have enough memory for each.  The overhead is so low that you don't notice much speed diff from running native Linux.  My wife needs Windows, and this is the setup she runs.

I got my brother using Ubuntu in a VM this way while we were talking on the phone.
Very easy and fast if you are booting Win.

It is a totally awesome free software experience.  Unlike WINE, it will for sure run everything.  Under VMWare, you are running the actual OS rather than an emulation.  This is not to put down WINE, but if you need a total solution, this is it.

Bob

---

### Post by tommcd on 2007-03-15
Here is my grub entry for zenwalk:
--------------------------------------------------------
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Zenwalk Linux (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/sda5 
initrd		/boot/initrd.splash
savedefault
boot
----------------------------------------------------------------
This was added automatically. When I installed zenwalk I mistakenly reformatted my ubuntu partition, so I had to reinstall ubuntu. You may need to add the kernel number after vmlinuz as in your ubuntu entries. In this case though it does not seem to be necessary.

---

### Post by Xappe on 2007-03-15
I would go for the chainload option mentioned by tommcd earlier. I've used that kind of setup with dapper and edgy (when edgy was under development) and now with edgy and feisty. This works very good and each distro manages it's own grub menu with kernel updates and so on...

---

