---
title: "Can you dual boot from different drives?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-03
Is it possible to dual boot from different harddrives? For instance, I have 3 drives; one is the windows OS and all my games and apps; one is my file drive where i save all my work etc; and one is just an extra drive I have. Can I install linux on the third drive and still have the grub menu come up and ask me which OS to boot?

---

### Post by taurus on 2007-02-03
It works just fine.

---

### Post by xpod on 2007-02-03
You can boot as many drives as you want as far as i know.
When you install Ubuntu it will install the grub to your mbr automatically so if you wanted just Windows again you would need to revert the mbr back again.

You can install the grub anywhere you like but this takes a little more effort and it`s so much easier just to go with the default options to start out with

---

### Post by PurplePenguin on 2007-02-03
I'm quadruple-booting from three hard drives. :D

---

### Post by -Ghost9- on 2007-02-03
I installed linux to my 3rd drive, but now when the computer starts it just goes straight to windows. No grub boot menu or anything. Was I supposed to do something else that I didn't do?

Also, I tried going into the boot menu and picking the HD i install linux to, to boot first but I just got an "error loading OS" message.

---

### Post by bodhi.zazen on 2007-02-03
You either need to change the order of HD boot in BIOS or install grub into the MBR of the first HD.

This should help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by -Ghost9- on 2007-02-03
> **bodhi.zazen said:**
> You either need to change the order of HD boot in BIOS or install grub into the MBR of the first HD.

This should help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

i tried following these instructions, but failed. 

When I did the find command, it said file not found. also, even when i tell the computer to boot from that same 3rd hd, it gives me the "Error loading OS" message.
I know it all installed to the 3rd hd since windows now doesn't even recognize that it's there. I'm getting increasingly frustrated. This feels like trying to learn a new language by jumping into the middle of someone else's conversation.

---

### Post by bodhi.zazen on 2007-02-03
Boot to the Ubuntu live (desktop) cd.

Open a terminal

Post the output of:```
sudo fdisk -l
```

One other tip:

You need to start grub with sudo

```
sudo grub
```

Then you can re-try the find command.

---

### Post by -Ghost9- on 2007-02-03
> Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19457   156288321    6  FAT16

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4664    37463548+  83  Linux
/dev/hdd2            4665        4865     1614532+   5  Extended
/dev/hdd5            4665        4865     1614501   82  Linux swap / Solaris

Also, i did the sudo grub command and tried to follow the directions again. It went through the setup with all positive responses, but when I restarted, nothing happened again. just went straight to windows. I don't think I understand how to access the mbr. The 40 gig drive is the linux drive, the 74 gig is the windows drive, and the 160 is my file storage drive where I keep all my saved work that I NEVER want to lose.

---

### Post by Buck2348 on 2007-02-03
This one's a little old but should still be good.  His list of linux partitions may be different than your setup.
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Buck

---

### Post by Tiburon41 on 2007-02-03
> **-Ghost9- said:**
> Is it possible to dual boot from different harddrives? For instance, I have 3 drives; one is the windows OS and all my games and apps; one is my file drive where i save all my work etc; and one is just an extra drive I have. Can I install linux on the third drive and still have the grub menu come up and ask me which OS to boot?

Absolutely.  I did it differently than others suggest, just in case I totally hated Linux, etc.  I installed Ubuntu to my second drive (Primary/Slave), and installed GRUB to a floppy.  I then set up the BIOS to look for the floppy, and I can pick my OS on boot without overwriting the MBR of my Primary drive.

---

### Post by broncbuster on 2007-02-03
> **Tiburon41 said:**
> ...  I installed Ubuntu to my second drive (Primary/Slave), and installed GRUB to a floppy.  I then set up the BIOS to look for the floppy, and I can pick my OS on boot without overwriting the MBR of my Primary drive.

How did you install grub to the floppy?  I see that i have a choice for the location of grub (hd0) is default, but i'm running all SATA drives as OS drives and 1 IDE drive for storage.  What do you change "(hd0)" to so it will install grub to the floppy?  Also, what do you change "(hd0)" to so it will install to the MBR of the other HDD?

---

### Post by Tiburon41 on 2007-02-03
> **broncbuster said:**
> How did you install grub to the floppy?  I see that i have a choice for the location of grub (hd0) is default, but i'm running all SATA drives as OS drives and 1 IDE drive for storage.  What do you change "(hd0)" to so it will install grub to the floppy?  Also, what do you change "(hd0)" to so it will install to the MBR of the other HDD?

When I did the install and it asked me where I wanted to install GRUB, IIRC, it also said you can install to the floppy with fdd (I think).  I also think (again, fuzzy memory and Linux n00b) to install to the second HDD it's hd1.  Don't take my word for it though.  I'm pretty sure about the fdd thing, but the hard drive, I'm not sure of.

---

### Post by broncbuster on 2007-02-03
Thanks, I'll give it a try.

---

### Post by bodhi.zazen on 2007-02-03
For a grub floppy take a look at supergurb:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If you want to make a grub floppy:

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

-Ghost9-

It looks like this should work:

```
sudo grub
```This gives you the grub prompt ....

Then:```
root (hd3,0)
setup (hd0)
quit
```

root (hd0,3) : When you entered your find command you should have gotten (hd0,3)

If that fails we need to look at /boot/grub/menu.lst (on your ubuntu root partition)

---

### Post by pseudonym on 2007-02-04
> **broncbuster said:**
> How did you install grub to the floppy?  I see that i have a choice for the location of grub (hd0) is default, but i'm running all SATA drives as OS drives and 1 IDE drive for storage.  What do you change "(hd0)" to so it will install grub to the floppy?  Also, what do you change "(hd0)" to so it will install to the MBR of the other HDD?
If you don't to bother with the floppy, do this -

1. Temporarily disconnect your IDE drive. You want to make things as easy as possible for GRUB.

2. Put windows on secondary SATA and the Ubuntu drive on primary (this may not be needed but it's what I do and it works).

3. Install Ubuntu on primary SATA and put GRUB in the MBR of this drive. Note that your windows MBR remains untouched this way.

4. When you finish the install you will be able to boot either OS. You will also note, if you look at the file /boot/grub/menu.lst, that GRUB 'mapped' the Windows drive to pretend to be the primary SATA drive, which is what Windows likes to be.

5. Reconnect your IDE drive and follow [this tutorial]("http://www.psychocats.net/ubuntu/mountlinux") to have it mounted in Ubuntu.

6. Enjoy Ubuntu! :)

---

### Post by -Ghost9- on 2007-02-04
> **bodhi.zazen said:**
> 
root (hd0,3) : When you entered your find command you should have gotten (hd0,3)


when i entered my find command, it gave me (hd1,0)

If this matters, the 74 gig drive is a sata, while the others are ide.

---

### Post by confused57 on 2007-02-04
> **-Ghost9- said:**
> when i entered my find command, it gave me (hd1,0)

If this matters, the 74 gig drive is a sata, while the others are ide.

Before you install grub to hd0(your Windows drive?), you might want to make sure you have the tools to restore your Windows mbr, if something goes wrong:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Also, I'd recommend that you burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The easiest way is to install grub to hd0 & most people don't have problems with doing this, but  there is always the outside chance there could be problems booting.

If you don't want to risk installing grub to your Windows mbr, you could opt to install grub to hd1(your Ubuntu drive)...it would require a little more manual configuration, but I believe it could be done if you can select in bios to boot first to the Ubuntu drive.  In fact, I don't believe it would hurt anything to try this first, & if it didn't work you could then install grub to the hd0 mbr.

If you choose the second option, open the grub menu at bootup, make sure your Ubuntu entry is highlighted, press "e" to edit, then change root (hd1,0) to root (hd0,0)...there's a menu at the bottom of the grub screen, but I think you press "b" to boot.   This change is only temporary, but if it works, then it's easy to make it permanent in your /boot/grub/menu.lst.  You'd then need to add an entry to boot Windows, similar to this:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I know this is a lot to "digest", but maybe it'll give you some ideas & options.

Here's how I have my system(s) set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Your setup would be somewhat different, but it'll give some instructions on how to edit your menu.lst, e.g. adding entries, making your grub menu visible at startup, changing the timeout, etc.

---

### Post by bodhi.zazen on 2007-02-04
> **-Ghost9- said:**
> when i entered my find command, it gave me (hd1,0)

If this matters, the 74 gig drive is a sata, while the others are ide.

Well, confused57 gave you some good advice, but perhaps overwhelming at first ...

You should be OK with :

sudo grub

...


root (hd1,0)
setup (hd0)
quit

...

Reboot and you should be able to boot all your OS ...

If not the links confused57 should sort it out, or of course re post ...

HTH

---

### Post by -Ghost9- on 2007-02-04
thanks for all the help. I managed to get to a point where grub loaded, but then when i picked ubuntu i got an error (17 i think) saying that the file system wasn't recognized. Sigh. I'm going to have to post-pone my attempt at getting linux up and running. As much as I want it to work, I'm getting to frustrated with it all, and i have lots of work i need to get to. I'll take a step back and try again after a while. I'm planning on doing some hardware upgrades, so maybe i'll try again after that. sigh. I think i would've been much more excited about all this if I could've gotten it up and running right away. oh well... I'll be back!!

---

### Post by rccharles on 2007-02-05
> **-Ghost9- said:**
>  the 160 is my file storage drive where I keep all my saved work that I NEVER want to lose.

I suggest you physically disconnect the drive when you are playing around.  & backup the data in case of a harddrive failure.

Robert

---

### Post by confused57 on 2007-02-05
> **-Ghost9- said:**
> thanks for all the help. I managed to get to a point where grub loaded, but then when i picked ubuntu i got an error (17 i think) saying that the file system wasn't recognized. Sigh. I'm going to have to post-pone my attempt at getting linux up and running. As much as I want it to work, I'm getting to frustrated with it all, and i have lots of work i need to get to. I'll take a step back and try again after a while. I'm planning on doing some hardware upgrades, so maybe i'll try again after that. sigh. I think i would've been much more excited about all this if I could've gotten it up and running right away. oh well... I'll be back!!

Here's a description of error 17 on Herman's Super Grub Disk Tutorial:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

Did you end up installing grub to hd0 or hd1?  Grub error 17 usually can be "fixed", it's definitely one of the more easily corrected...there's plenty of knowledgable people here who should be able to get you up & running when you're ready to try again...bodhi.zazen has given you some great advice...Herman's probably the most knowledgable about boot loaders on the forum, along with adrian(who developed the Super Grub Disk), so there is no dirth of knowledgable resources here.  See you later.

---

### Post by -Ghost9- on 2007-02-05
> **confused57 said:**
> Here's a description of error 17 on Herman's Super Grub Disk Tutorial:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

Did you end up installing grub to hd0 or hd1?  Grub error 17 usually can be "fixed", it's definitely one of the more easily corrected...there's plenty of knowledgable people here who should be able to get you up & running when you're ready to try again...bodhi.zazen has given you some great advice...Herman's probably the most knowledgable about boot loaders on the forum, along with adrian(who developed the Super Grub Disk), so there is no dirth of knowledgable resources here.  See you later.

hmm. that does seem like a more or less easy fix. thanks for all the help. i'll try again.

---

### Post by -Ghost9- on 2007-02-05
alright, i'm going to try dual booting again because I just can't give up. Is there a specific way i should defrag to make sure everything works right? I have a fresh install of windows since yesterday. last time i tried dual booting on the same drive it worked, but I noticed a significant slow down in windows loading.

---

### Post by confused57 on 2007-02-05
> **-Ghost9- said:**
> alright, i'm going to try dual booting again because I just can't give up. Is there a specific way i should defrag to make sure everything works right? I have a fresh install of windows since yesterday. last time i tried dual booting on the same drive it worked, but I noticed a significant slow down in windows loading.
I doubt if you need to defrag with a new install of Windows, but AFAIK there's no special defragging...you could defrag once just to be on the safe side.

If you still want to try installing Ubuntu on your other hard drive, this may work:
   Set your hard drive boot order in bios to boot hdd(drive where you're going to install Ubuntu) first and set your sata drive(with Windows) as the 2nd hard drive boot device.  You'd need to leave your system set up this way after installing Ubuntu, if you want to boot Windows from Ubuntu's grub.  Even set up this way, you can boot directly to Windows by setting your SATA as the first hard drive to boot.
  
Install Ubuntu to your hdd, then boot into Ubuntu & add the entry to boot Windows(I think I've already given this link):
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902) 

So it's your choice, install Ubuntu onto the same drive as Windows or install on a different hard drive.  Installing on a different hard drive, if one OS fails, just set your bios to boot the other drive...booting first to Ubuntu will enable you to boot Ubuntu or Windows.
I can't guarantee it'll work, but it doesn't take that long to install Ubuntu to find out.

---

