---
title: "beige g3 install - errors on installing base system"
date: 2005-02-03
forum: Apple PPC Users
---

### Post by Elsifer on 2005-02-03
Well, I can get the cd to boot, the installer runs, I configure language, I get a dhcp assigned address, but the installer errors on Installing Base System, no installable cdrom was found and no valid mirror was configured.

I am using the hoary-live-powerpc.iso

So, basically, the installer is confused, as I can partition the disk, the installer runs, so the cd is found, and I get a dhcp ip. I can do an ifconfig but no ping. dmesg also returns hardware happiness.

Now I do have a 12Gb ide disk in this unit. 500mb is for OS9.1, 11Gb for / and 500Mb for swap.

I used the "use max empty continous space" option in the partition tool.

Is the installer confused to the size of the partitions? The druid did format the partitions, and I can mount them.

Oh, and I did do a cdrom integrity check, it passed.

Any ideas?


Well, since then I downloaded the warty install cd, and it works perfectly.
Meh, I guess its a bug in the hoary installer. *shrug*
No worries. Should I file a bug report and include the logs?

---

### Post by betterok5 on 2005-02-04
I would be extremely grateful if you would tell how you got your beige g3 to boot the live cd.  I have a similar machine and can't get past the boot kernal.  I get a message that it cannot find root filesystem.  I downloaded the image and burned it with Toast.  I believe it is a good disk from the filenames.  I have been using Bootx as I have been informed that it is the only way to boot old world macs.  The boot.msg file on the cd says to hit enter or type in linux video=ofonly but I never get far enough along to get a command line prompt.  Any help from anyone would be much appreciated.  I am beginning to think it is impossible to run linux on the mac.  
Thanks in advance
kk

---

### Post by betterok5 on 2005-02-04
[QUOTE=Elsifer]Well, I can get the cd to boot, the installer runs, I configure language, I get a dhcp assigned address, but the installer errors on Installing Base System, no installable cdrom was found and no valid mirror was configured.

I am using the hoary-live-powerpc.iso

So, basically, the installer is confused, as I can partition the disk, the installer runs, so the cd is found, and I get a dhcp ip. I can do an ifconfig but no ping. dmesg also returns hardware happiness.

Now I do have a 12Gb ide disk in this unit. 500mb is for OS9.1, 11Gb for / and 500Mb for swap.

I used the "use max empty continous space" option in the partition tool.

Is the installer confused to the size of the partitions? The druid did format the partitions, and I can mount them.

Oh, and I did do a cdrom integrity check, it passed.

Any ideas?


Well, since then I downloaded the warty install cd, and it works perfectly.
Meh, I guess its a bug in the hoary installer. *shrug*
No worries. Should I file a bug report and include the logs?[/QUOTE]
 I would be extremely grateful if you could tell me how you got your beige g3 to boot the live cd.  I have a similar machine and have had no success with it.  I am using the hoary live cd and bootx since I am given to understand that bootx is the only way to boot an old world mac into linux.  Any help anyone can provide would be most appreciated.  I am beginning to think it is impossible to run linux on a mac.
KK

---

### Post by Elsifer on 2005-02-05
Well, its not impossible to run linux on an oldworld mac, its just an 'interesting' experience.

I use BootX, install it, etc, etc, as per the documentation.
From the Ubuntu cd, I copy the /install/powerpc/initrd.gz and vmlinux files to the Linux Kernels folder that is put into the System folder in OS9or8.
I then set BootX to boot the vmlinux kernel, and use the initrd.gz as the ram disk.
I also ran the "SetG3Cache" script, so I can enable the cache setting in BootX.
I didnt use the kernel parameters, and the system booted.

I am currently trying to figure out what works for me, and try to use the OldWorldMacInstall document in the Ubuntu wiki ([http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)).

What I can do is install the system, I just cannot seem to be able to boot the installed system. So, using trial and error, some googleing, and reading of this forum; get my G3 Gossamer to boot Ubuntu.

I have experience getting NetBSD and gentoo running on this old guy. But I have a 12.5 Gb ide disk, and I junked the old scsi unit. I cant remember offhand, but I have the rev of the systemboard that allows for a master & slave ide drive on the primary controller. Even though my cdrom is on the secondary. Lots info on the netbsd site about the hardware, and what or what does not run.

And as I type this, I have managed to get the system to boot!
YAY!
Same thing applied, I copied the kernel and initrd from the installed Ubuntu partition, to my OS9 partition, renamed the intall kernel and initrd to 'install-vmlinux' & 'install-initrd'. And kept the vmlinux and initrd for the installed system the same.
BootX config is the new kernel, no kernel parameters, and no ram disk!
Simple!

The only thing I did differently, was scp the kernel and initrd from the install system to a different box rather than do the pivot_root stuff. And then http download into OS9 and config BootX.

Sorry for such a verbal post, but imho, coming from NetBSD, to Gentoo, now to Ubuntu on this G3; Ubuntu rocks, its easy, its simple, it works. Gentoo and NetBSD worked too, it was just a *lot* more work. And a stock Debian install, well, its just as tricky. Ubuntu has made this simple. The documentation just needs a little tweak to make it more so!

Good Luck!

---

### Post by betterok5 on 2005-02-05
Thanks for all your help!!  I haven't tried your advice yet but most of it makes sense.  I had not known to put initrd.gz into the kernal folder.  Using bootx I was not able to get the cd mounted using vmlinux from the Ubuntu cd.  I used instead vmlinux2.4 from Debian.  That mounted the cd but kernal paniced when it couldn't find init.  I have made upteen installations of Debian, most of which sorta work but never x-windows.  I guess you might say it has been a learning experience.  That was why I wanted to try a live cd thinking maybe if someone else made the install it would be more correct.  Until a couple weeks ago debian had been my only exposure to linux.  It was then that I cobbled together a pentium MMX box with an extra drive and installed Libranet from a couple of cds my brother gave me.  No muss, no fuss, just wind it up and let the installer do its thing.  That one is really short on memory and the drive isn't big but it works great.
I guess I still have a few questions for you.  
Does the kernal find the init automatically if you put it in the kernal folder?
Where do you get the SetG3Cache script and what do you assail with it?
The mac I am currently trying to get to run linux is a 300 mhz G3.  It has 576 mb ram and a 80 meg hard drive and a dvd/cd burner.  The drives are all ide in this one.  I have installed linux onto an external scsi, so far leaving the main drive alone mostly because I haven't gotten the ambition to back everything up and reformat.  I probably shouldn't have dolled it up so but it really is a sweet running machine.  As with the rest of my life, I run junk for computers.  I try to get them here for under 100 dollars and then add parts as needed.  At this point in history there is some serious computing horsepower out there for not a lot of money if you don't really need to have the newest and fastest.  
Anyway thanks again for all your help and good luck with yours.
Excuse my verbosity
kk

---

### Post by Elsifer on 2005-02-05
[QUOTE=betterok5]Does the kernal find the init automatically if you put it in the kernal folder?[/QUOTE]
Yes, I dont understand the magic behind it, but it does seem to find the init and the root=/dev/foo info. I cant explain it, I tried it on a wild hunch, and it worked. One of the ppc dev's will be able to answer that one for us. If that is the answer you are looking for, I assume that you mean when the system is already installed and you are trying to get it to boot of the hda rather than the cdrom/ramdisk.

So basically when you want to boot of the cd, the kernel and the initrd.gz options have to be set.

If you want to boot of the hda (or sda I guess if you have it, for the benefit of others reading this), just the kernel option needs to be set, no initrd/ramdisk and no kernel parameters.

[QUOTE=betterok5]Where do you get the SetG3Cache script and what do you assail with it?[/QUOTE]
The SetG3Cache is in the scripts folder in the unpacked BootX. Basically the control panel extension has to be installed, the Linux Kernels folder put into System, and the machine rebooted. Then the script can be run, so the toggle can be enabled. Just double-click it. MacOS is very visual, if the icon has some sort of picture, then actuating it can do stuff, if its just a blank rectangle, good luck, open your app and then open the file manually.

[QUOTE=betterok5]The mac I am currently trying to get to run linux is a 300 mhz G3.  It has 576 mb ram and a 80 meg hard drive and a dvd/cd burner.  The drives are all ide in this one. [/QUOTE]
Pretty much the same as mine, 300mhz and a 12.5Gb ide drive, with a regular ide cdrom. I am jealous of your burner!

I hope all this helps!
I am writing this in my freshly booted install! It's worth it!

Now to get better than 800x600....

---

### Post by betterok5 on 2005-02-05
Tried what you recommended and some other stuff too but still no cd boot.  The best I can say is that I get a variety of errors just before the kernal panic.  As before if I use vmlinux2.4, the cd mounts just before losing track of the init.  Setting the ramdisk option kills the init.  vmlinux can't find the disk.  One detail that I do notice is that when using the vmlinux2.4 kernal and the cd mounts it is identified as iso9660.  When I burnt the disk toast called it a hfs/iso9660 hybrid.  Can that be a factor?

I am surprised you had so much trouble getting your hard drive to boot.  That always worked for me.  First boot after the install I have to give it the vulcan death grip (cmd-option-P-R) to get it started but thereafter no problems whatsoever, just put the pathlist in bootx and hit linux. That seems to work with any of the kernals.  Seems kinda strange to have 2 machines so similar and have such varied, even opposite results.  Oh, well.

>Pretty much the same as mine, 300mhz and a 12.5Gb ide drive, with a regular ide cdrom. I am jealous of your burner!<

That was probably an extravagance.  I had no burner at all before and figured I should do something.  I got it from Other World Computing.  It is supposed to be nearly the same as an apple superdrive.  I have yet to burn a dvd.  I thought as long as I was getting I might as well have some capability.  It boots by holding C (with macos disks).  One of the things I had hoped to accomplish is to burn from linux.  That has not worked out yet either.  The version of cdrecord that I have only looks at the scsi bus and the burner is ide.  I got a package that claims to get ide too but have not yet installed it.  Having trouble getting it onto the apt-get database (I think that was the hangup).  Maybe someday.....
kk

---

### Post by Elsifer on 2005-02-05
Well, I have to admit, I made a pretty big mistake in my BootX config. I had posted earlier that I only added the vmlinux to BootX to make the system work. Well, I'm wrong.
I also added a section to the InstallOnOldWorldMacs wiki.
[https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

Here is what does work for me:

Kernel: vmlinux (renamed from the uber long vmlinux-ubuntu-numericalstuffhere)
Options, RAM Disk: initrd.img (renamed from the uber long initrd.img-ubuntu-numericalinfohere)
All four checkboxes on (Set G3 cache, Force SCSI ON, Force video settings, Use specified ram disk)
And no kernel parameters.


Now I am fighting with the onboard ATI Rage 3D Pro 215GP, and the ati X driver going only to 800x600.

---

### Post by Elsifer on 2005-02-05
[QUOTE=betterok5]When I burnt the disk toast called it a hfs/iso9660 hybrid.  Can that be a factor?[/QUOTE]

Hmm, good question. I am not sure, I just right clicked the iso, and "Open with Toast".

Someone else had an issue with a burned Hoary cd on this forum, and I havent been able to check his request and verify anything. AFAIK, there was no hfs hybrid stuff when I burned mine. *shrug*

When I open the warty-release-install-powerpc.iso with Toast, it shows as a copy function, and a straight Image File action. Maybe your downloaded iso is corrupt? md5sum it.

---

### Post by betterok5 on 2005-02-06
Maybe that is the difference.  The first disk in my Debian set is a hybrid also and you can't blame that one on me.  That was the way it came.  I can only guess at it but I suspect that to be bootable it needs something that looks like mac os to start from.  I started by running Toast and using from the 'other' menu:  'disk image', then clicked on the 'select' button and pointed it towards my iso.
My Debian disk one got scratched so I downloaded an image and burned it in the same manner and it worked ok to install from.  I am not sure if that one is bootable at all.  I always started from a pair of floppies to install.
I didn't md5sum the image so that may be the problem.  There is nothing obviously amiss though.  Would be worth a try.  At least I have been using rw disk so I don't burn so many coasters.

---

### Post by trash on 2005-02-18
I really wish i'd taken notes while installing Warty on my G3,266(all in one machine)... i don't remember having any of the problems you're having with the install.. though i will double check what ram disk size i used.. i'll post later... for now here's how i got 1024x768 @70hz

Section "Device"
        Identifier      "ATI Technologies, Inc. 3D Rage Pro (215GP)"
        Driver          "ati"
        BusID           "PCI:0:18:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       56 #28-49
        VertRefresh     70 #43-72
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. 3D Rage Pro (215GP)"
        Monitor         "Generic Monitor"
        DefaultDepth    16 #24
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection
EndSection

---

### Post by trash on 2005-02-18
It doesn't seem like i used any extra parameters but i could be mistaken, all i do know for sure is that the force video and use specified ramdisk were the only boxes i checked and I used ramdisk size 8192. Hope it helps.

---

### Post by hndrcks on 2005-02-18
I completed an install on a AIO 233 yesterday - everything went swimmingly because I had installed a $20 usb card in a pci slot and was able to copy the final kernel / initrd to a usb memstick before rebooting after install; then I put it in BootX folder on restart. 

My BootX parameters are everything clicked OFF. Nothing selected.  Boots 1024x768 x millions every time. I was expecting this thing to be dog slow but it's actually quite snappy...

---

### Post by trash on 2005-02-18
i think i used the force video because it may have been selected by default... does sound like you had an easy go of it hndrcks.
Ya Ubuntu is awesome for this machine, i now have 192mb of ram but i'll get more soon and i'm so glad you mention the usb card/stick.. thats on my list too! Seeing as you had no problems with it what make is it?

thanks.

---

### Post by hndrcks on 2005-02-18
Um... the pci usb card is a no name with an opti chipset. USB 1.1 very basic. Every memory stick I have used since seems to work fine!

Ohhh - and it may be my avatar that ensures easy installs!  :wink:

---

### Post by markov035 on 2005-11-11
[QUOTE=Elsifer]Well, I have to admit, I made a pretty big mistake in my BootX config. I had posted earlier that I only added the vmlinux to BootX to make the system work. Well, I'm wrong.
I also added a section to the InstallOnOldWorldMacs wiki.
[https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

Here is what does work for me:

Kernel: vmlinux (renamed from the uber long vmlinux-ubuntu-numericalstuffhere)
Options, RAM Disk: initrd.img (renamed from the uber long initrd.img-ubuntu-numericalinfohere)
All four checkboxes on (Set G3 cache, Force SCSI ON, Force video settings, Use specified ram disk)
And no kernel parameters.


Now I am fighting with the onboard ATI Rage 3D Pro 215GP, and the ati X driver going only to 800x600.[/QUOTE]
Had the smae prob in YDL.
Edited the X config and it worked ..

I can't boot afte the install ...
Did all things that I found on the wiki,
but ...

if you boot from /dev/sda2, where do you put that ??
And after install, do you still need a ramdisk ??
then you can't put /dev/sda2 as boot partition ??
Are you always using live cdrom??
sometimes they say:
put 
root=/dev/sda2
but this doesn't work either.

Ydl was fine, but audio didn't work on the beige G3/266/196Mb...
I chose ubuntu, because debian packages install on it ..

---

