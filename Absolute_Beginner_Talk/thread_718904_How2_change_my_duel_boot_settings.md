---
title: "How2 change my duel boot settings?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Ozzz on 2008-03-08
Doing great so far from reading posts. I got Ubuntu 7.1 installed on external USB drive. I managed to get wireless printing thru desktop XP to work and managed to see shared files/folders on desktop thru wireless. Also got all audio and vido working after I installed all the updates.

OK - During install my MBR on my laptop with XP Professional was changed. In order to boot the laptop into XP I now need to have the external USB drive with Ubuntu plugged in so I get the duel boot option menu, otherwise the boot sequence says no operating system found (scared the heck out of me at first, thought i lost everything during install).

Late last night I discovered a comment somewhere that during the install process, just before it actually begins the install, there is a box labeled "Advanced". If you click the box it gives you the option to NOT write to the XP MBR. Wow, a bit too late and should not be hidden like that. Anyway ...

[COLOR="RoyalBlue"]I need to correct whatever I can so that the external USB does NOT have to be plugged in in order to select the duel boot option.[/COLOR]

I know I can boot from my XP Professional install CD and repair the MBR back to its original state, but then what happens?

I want to be able to grab the laptop and go and have my XP boot normally without having to tote along my USB drive just to do it. I want to be able to run Ubantu when I plug the USB drive in.

Any words of wisdom on just how I can accomplish this would be GREATLY appreciated.

Thx

---

### Post by justsomedude on 2008-03-08
Tricky.

GRUB is installed to the MBR of your internal drive, the files GRUB needs to read in order to boot any of your systems are located under /boot on your external drive.

If you fix the MBR with your XP install CD, Windows will boot normally, but Ubuntu won't.


Idea: change your boot order to boot from USB first, your internal drive second. If your Computer cannot boot from USB, ignore the rest of my post.

Reinstall GRUB to your external drive:

```
sudo grub-install /dev/hdb
```

[color=red]CAREFUL[/color]: You have to replace /dev/hdb with the correct path for your external drive!!!

Then, you can fix the MBR of your internal drive with your Windows install CD  (unplug your external drive while doing this).

If all went well, Windows will boot normally when your external drive is unplugged. If it is plugged in, GRUB will appear and offer you a choice. 

If not, you're screwed. :lol:

Or report back here.

Try at your own risk. And backup your Data first!!!

---

### Post by ghost_ryder35 on 2008-03-08
Reinstall Ubuntu and mount **/boot** on the internal drive :)

---

### Post by ghost_ryder35 on 2008-03-08
hmmm... Maybe 
Copy your current /boot to a flash drive...
Boot up in to the Live Ubuntu CD, open Partition Editor, create a **/boot** partition on the internal drive  Then reinstall grub like just some dude said.  Then copy your **/boot **from the flash drive to the new **/boot **location on the internal drive

---

### Post by Duck2006 on 2008-03-08
Repair the mbr of your internal drive and then install grub on the external drive mbr

To install grub to the usb drive boot the live cd and in the terminal

sudo grub

find /boot/grub/stage1   " this will come back with a (sd1,0) or some thing like that

root(sdx,y)  "with what the line came back with change x,y with

setup (sd1)

quit

for more reading there is this.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Ozzz on 2008-03-08
following your tip, this is what I have:

sudo grub

find /boot/grub/stage1 (this returns hd1,2 as a result)

Looking at my prior notes - WinXP is hd0,0 and Linux is on hd1,2.

Also, (I probably should have mentioned this earlier) the external USB drive is a 160 GB partitioned in half. When I installed Ubantu it did install to the USB drive but which particular partition I don't know for sure.

---

### Post by Duck2006 on 2008-03-08
With the usb drive pluged in, from the terminal type.

sudo fdisk -l

That should tell you as to where the ubuntu install is. post the outputs here.

---

### Post by Ozzz on 2008-03-08
> **Duck2006 said:**
> With the usb drive pluged in, from the terminal type.

sudo fdisk -l

That should tell you as to where the ubuntu install is. post the outputs here.

trg@trg-laptop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30f930f8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9420    75666118+   b  W95 FAT32
/dev/sda2           19128       19457     2650725   82  Linux swap / Solaris
/dev/sda3   *        9421       18797    75320752+  83  Linux
/dev/sda4           18798       19127     2650725    5  Extended
/dev/sda5           18798       19127     2650693+  82  Linux swap / Solaris

Partition table entries are not in disk order
trg@trg-laptop:~$

---

### Post by jesusfreak107 on 2008-03-08
ah, easy. we do this all the time at our house.  Just boot Windows into recovery mode, do fixmbr, boot off of windows, and install GRUB onto windows itself (you can download it from somewhere, i forget. google it).  voila!!!:guitar:

---

### Post by Duck2006 on 2008-03-08
> **Ozzz said:**
> trg@trg-laptop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30f930f8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9420    75666118+   b  W95 FAT32
/dev/sda2           19128       19457     2650725   82  Linux swap / Solaris
/dev/sda3   *        9421       18797    75320752+  83  Linux
/dev/sda4           18798       19127     2650725    5  Extended
/dev/sda5           18798       19127     2650693+  82  Linux swap / Solaris

Partition table entries are not in disk order
trg@trg-laptop:~$

Your linux partition is on (hd1,2), so yes it returned the with the wright partition.

---

### Post by ODF on 2008-03-08
Editing it with 

```
sudo gedit /boot/grub/menu.lst
```

Is pretty easy.

---

### Post by Ozzz on 2008-03-08
> **jesusfreak107 said:**
> ah, easy. we do this all the time at our house.  Just boot Windows into recovery mode, do fixmbr, boot off of windows, and install GRUB onto windows itself (you can download it from somewhere, i forget. google it).  voila!!!:guitar:

Bless you all for the help! I've been reading since last night (til 1am) and all day, following one link after the other. I thought I would have to go into recovery mode to patch my MBR but didn't want to risk not being able to get back into Ubantu since I have it tweeked and everything (including wifi printing) is working so smoothly.

Thanks for the very helpful link about grub posted above too, very good reading. As soon as I find a where/how to install GRUB onto windows i'll be a very happy camper.

---

### Post by Ozzz on 2008-03-08
> **ODF said:**
> Editing it with 

```
sudo gedit /boot/grub/menu.lst
```

Is pretty easy.

Thx - I used that code early this morning to create a "backup" copy just in case I messed things up. It looks like I do not need to edit it at this point from the earlier posts - is that correct?

---

### Post by ODF on 2008-03-08
Your menu.lst for windows shoud looks like this : 

```
title		Windows
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

(hdX,X) depend of your hd and partition.

I dont really know if you need or not but I tried to 'sudo grub' and found it more difficult than editing my menu.lst

All you need to know is ex (hd0,2) is first hd and third partition.

Have luck.

---

### Post by Duck2006 on 2008-03-08
From post #8 win is on hd0,0

---

### Post by Ozzz on 2008-03-08
> **Duck2006 said:**
> From post #8 win is on hd0,0

That's correct. I'm looking for a GRUB to install to my internal WinXP professional hd.
Before I begin any MBR repair and am still logged into Ubantu via external drive; is there a terminal command I can run to install GRUB to my internal or is the GRUB used to install on my win drive an .exe type file.??

---

### Post by ODF on 2008-03-08
> **Ozzz said:**
> That's correct. I'm looking for a GRUB to install to my internal WinXP professional hd.
Before I begin any MBR repair and am still logged into Ubantu via external drive; is there a terminal command I can run to install GRUB to my internal or is the GRUB used to install on my win drive an .exe type file.??

Well, since your linux hd is the primary boot, your grub will be promted first. When selecting your windows in the linux grub it will boot your hd/partition with windows in it like default. It will load the windows boot menu if you've more than one windows installed. If not, it will load like there's no linux at all.

---

### Post by Duck2006 on 2008-03-08
Do you want to write to the MBR of the internal drive? 
If you don't want to write to the MBR of the internal drive you can use some thing like wingrub.

[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

This is a how to.

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

### Post by Ozzz on 2008-03-08
> **Duck2006 said:**
> Do you want to write to the MBR of the internal drive? 
If you don't want to write to the MBR of the internal drive you can use some thing like wingrub.

[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

This is a how to.

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

I believe that to get windows to boot 'normally' i have to fix the mbr there. Then run Windows without the external drive connected. (maybe with it connected, but it will boot into windows if I don't select F12 (boot other OS).

If i want to run Linux i can just power off Windows, plug in the external drive and power back on the computer, at which point it gives me the duel bootup option.

I guess what 'I" think is happening and what I am trying to correct is that in order to boot at all right now I must have the external drive plugged in because the bootloader itself is on the external (without repairing the original internal hd mbr). - now i am confusing my - LOL

---

### Post by Duck2006 on 2008-03-08
If you don't have a win xp cd have you tried super grub live cd to fix your MBR.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Ozzz on 2008-03-08
> **Duck2006 said:**
> Do you want to write to the MBR of the internal drive? 
If you don't want to write to the MBR of the internal drive you can use some thing like wingrub.

[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

This is a how to.

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

Your links are exactly what I am looking for. Thanks. I think it will work. I just opened and am starting to read it now. - I'll followup shortly.

---

### Post by Ozzz on 2008-03-08
> **Duck2006 said:**
> If you don't have a win xp cd have you tried super grub live cd to fix your MBR.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I didn't until yesterday when I downloaded it from my son's server (huge!). Toshiba was not kind enough to give me copy when I got bought this thing. I also got a copy of supergrubdisk_0[1].9677.iso , wasn't aware that it might fix my mbr; i still need to burn the image.

---

### Post by Ozzz on 2008-03-09
Update:

I used the WinCD to patch my MBR. Loaded WinGrub and set the parameter in the window's boot.ini file and rebooted. I then got the following error when I tried to boot into XP:

Boot Error:
Booting Microsoft Windows XP Professional
root (hd0,0)
filesystem type is NTFS, partition type 0x7
savedefault
error 26: disk read error
Press any key to continue ...

As you can see, I was able to boot into Linux just fine.
Any suggestions at this point? Could it have something to do with the line 'savedefault' ? This 'savedefault' line in my menu.lst file is commented out (by default) btw.

---

### Post by Ozzz on 2008-03-09
> **ODF said:**
> Your menu.lst for windows shoud looks like this : 

```
title		Windows
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

(hdX,X) depend of your hd and partition.

I dont really know if you need or not but I tried to 'sudo grub' and found it more difficult than editing my menu.lst

All you need to know is ex (hd0,2) is first hd and third partition.

Have luck.

After applying the mods noted in previous post, i powered off, unpluged the external (linux) hd and booted into windows by selecting it from duel boot menu option. Windows booted normally. I then looked in the folder, C:\grub and the <i>menu.lst</i> file there. Below is what is in that file:
timeout 10
title windows at (hd0,0)
root (hd0,0)
chainloader +1

that's it... nothing at all like the output shown above.

At this point I can now (after a few failed attempts) grab the laptop and go and boot into XP as normal. If I want to boot into Linux, I grab my external USB; or plug it in and reboot to WinGrub. I think i am at 99% complete - it is just the boot error message i noted earlier about savedefault and the generated error 26. I have a feeling that the menu.lst file on my C:\Grub is not complete or in error because of the savedefault message.

---

### Post by jesusfreak107 on 2008-03-10
No offense to ODF, but this is how all 4 grubs on my computer show my Windows, along with both of the grubs on our family computer, and Dad's grubs.  and they all work.

---

### Post by perixx on 2008-03-10
Strongly recommending this site here, where you'll find lots of very very useful information regarding MBR/booting and Grub problems:
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

perixx

---

### Post by Ozzz on 2008-03-10
> **jesusfreak107 said:**
> No offense to ODF, but this is how all 4 grubs on my computer show my Windows, along with both of the grubs on our family computer, and Dad's grubs.  and they all work.

Thx for the feedback on that; I can rest a little more easily now. I haven't restarted my system since yesterday (old habit of leaving things powered on), but the last boot did work. Appreciate all the input and help!:)

---

### Post by Ozzz on 2008-03-10
> **perixx said:**
> Strongly recommending this site here, where you'll find lots of very very useful information regarding MBR/booting and Grub problems:
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

perixx

Thx for the link. I did find it yesterday on my desktop was spent a lot of time reading through it. I was going to bookmark but before I got around to it last night something in Outlook went bonkers and forced a hard system reboot in XP. I had to reboot that think three times (desktopXP again) before it totally recovered. I have now bookmarked it in my Linux laptop - thanks!

---

