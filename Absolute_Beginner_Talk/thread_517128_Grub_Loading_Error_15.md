---
title: "Grub Loading: Error 15"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-08-04
I was having trouble with Edgy not wanting to play DVDs, so decided to upgrade to Fiesty 7.04 - apparently that was the wrong thing to do. Now, after re-installing 3 times I get a "Loading Grub: error 15" and the machine won't load software. Same problem even after re-installing each time. What's the deal?

---

### Post by tcoffeep on 2007-08-04
I believe this forum thread from the gentoo forums will help you :

[http://forums.gentoo.org/viewtopic-p-3056992.html](http://forums.gentoo.org/viewtopic-p-3056992.html)

I hope this helps. Don't give up. I've went through this bullcrap too. I just reinstalled using the alternate cd.

---

### Post by lwalper on 2007-08-04
Thanks for the link. That's all interesting, but for me, gobbldygook. Don't have a clue what they're talking about.

---

### Post by lwalper on 2007-08-04
OK, so went back to Edgy 6.10, did a full repartition and installation. Now I get an error 17 and hangup.

Do I need to do a low level drive format?--to get rid of any and all drive partition information?

---

### Post by lgambett on 2007-08-04
For some reason your GRUB looks for the kernel image in the wrong place. Before reinstalling try to understand what is happening; stop the boot process pressing ESC when asked, then select the top row of the GRUB menu (Ubuntu, kernel 2-6-20-16....) and press e for edit. The first row (i.e. root(0,0)) points to the drive and partition where GRUB looks for the kernel image. Check if this is correct (ie first partition on first IDE disk should be root(0,0)).

---

### Post by lwalper on 2007-08-04
There is no opportunity given to press ESC. I get:

1. The POST (which includes an opportunity to enter the BIOS setup by pressing DEL)
2. Messages that say

Verifying DMI pool data .........
Boot from CD: (which I don't do)
GRUB Loading stage 1.5

GRUB loading, please wait
Error 15

Well, if I can ever get to that point again I'll try it. I'm currently in the process of re-installing 7.04. The installation has hung a couple of times at 29%, now at 57% -- everything's locked up. Try again . . .

---

### Post by tcoffeep on 2007-08-04
have you used gparted?

---

### Post by tcoffeep on 2007-08-04
Another quick suggestion :

When I started 2 or 3 monthes ago, [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php), was the resouce I worshipped, and still do. It should help you in all respects. Try it out.

---

### Post by lwalper on 2007-08-04
gparted? No, what's that?

I've booted with the CD and have -- I guess -- gparted open. It shows three partitions (which I did make)

hda1 - ext3 format - of 65.19Gb - mountpoint - /media/dosk-1
hda2 - fat32 format - of 4.66Gb - mountpoint - /media/disk
hda3 - linux swap - 6.84Gb

When I created the partitions I was forced to make one partition active with a mount point of / -- which I did (hda1).

Should I look around for a MBA editor and completely reinitialize the HD, beginning from scratch and try a reload? Maybe the MBA is messed up?

---

### Post by AlexenderReez on 2007-08-04
> **lwalper said:**
> gparted? No, what's that?

I've booted with the CD and have -- I guess -- gparted open. It shows three partitions (which I did make)

hda1 - ext3 format - of 65.19Gb - mountpoint - /media/dosk-1
hda2 - fat32 format - of 4.66Gb - mountpoint - /media/disk
**hda3 - linux swap - 6.84Gb**

When I created the partitions I was forced to make one partition active with a mount point of / -- which I did (hda1).

Should I look around for a MBA editor and completely reinitialize the HD, beginning from scratch and try a reload? Maybe the MBA is messed up?

gparted livecd is a livecd contain gparted utilities only...hmmm....please make linux swap below 1 g..it is just backup for RAM(random access memory) and it can't support to much so you just waste a lot of your space for that...

---

### Post by AlexenderReez on 2007-08-04
> **lwalper said:**
> I was having trouble with Edgy not wanting to play DVDs, so decided to upgrade to Fiesty 7.04 - apparently that was the wrong thing to do. Now, after re-installing 3 times I get a "Loading Grub: error 15" and the machine won't load software. Same problem even after re-installing each time. What's the deal?

to play dvd you need codec for that...and not all player can play it....hm...i suggest you to try smplayer ...but before that please install dvd codec from > [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by tcoffeep on 2007-08-04
My partition is set up like this :

110 GB For Ubuntu Feisty 7.04 (EDIT : Ext3)
2 GB for Linux Swap (EDIT : LinuxSwap)
and about 8 GB unused space.

(I use 2 GB for swap in case my memory fails)

---

### Post by belikralj on 2007-08-04
You're right it's probably something to do with the MBR and there are posts on grub and error 15, I don't remember exactly how it was fixed but I know it involved the Super Grub Disk or something like it. You probably need to rewrite the MBR and somehow reinstall grub. This happened to me and I think the cause was that I have overwritten the grubs installation or some part of it but I cant remember the details. It's 4am and I can't concentrate. Hope this helps at all. Good night

PS  I too think 6.** GB is WAAY too much swap space, 2GB is the most I would put. Unless you have 4GB RAM then put 4GB though I doubt you would even need swap.

---

### Post by lwalper on 2007-08-05
I may be going the long way around, but found a MBR utility that was supposed to run in Linux - could find the file in the file manager (which identified it correctly as an executable file) but for some reason, when I double clicked on the file, it would not run. So, . . .

Stuck in my trusty Win2K boot CD, have repartitioned and installed Win2K and will now attempt to use a MBR utility for that OS. After all has been zeroed out, will then attempt to re-install 7.04. Keep your fingers crossed!!

---

### Post by lwalper on 2007-08-05
Well, at least it's different.

The Ubuntu install again hung at 29%. So I restarted the machine with the boot CD -- the partitions appeared to be in place with files in the appropriate places.

Since the installation hung at 29% there was no assurance that all the files were copied correctly so I chose to repeat the installation. This time everything seemed to complete as planned with return to the desktop and display of the partitions on the desktop.

Restarted the machine (without the boot disk) and . . . oops -- the POST runs, the cursor mooves past the "boot from CD" area as though soemthing exciting is going to happen, but alas, no joy. Now the message that the GRUB is loading doesn't even come up and the machine is hung.

What now?

---

### Post by yamyogurt on 2007-08-05
I had the same problem... This is my experience. After installing Ubuntu about three times my install disk (that I burned) started to flake out. The install would get to about 35% and give me an error, and when I restated my computer I got the grub 15. Because I was duel booting Xp and Ubuntu I could not access either. I just had to burn a new install disk and boot from Cd and the problem was fixed.

*[EDIT]*
 I suggest just trying a new install disk before of trying to rewrite anything.

---

### Post by lwalper on 2007-08-07
So now I've

1) re-downloaded the .iso file, burned a new CD.
2) re-partitioned the entire disk / installed Win2K in 3Gb of space (FAT32 format)
3) re-installed Ubuntu 7.04 in the remaining free space (etc3 format) with a 1.2Gb swap. Mount point for Ubuntu is the \ native Ubuntu root.

Have now rebooted -- Win2K loads nicely, but no option to boot into Ubuntu. I thought a boot manager would kick in there somewhere? Should I have made the mount point the Win2K partition?

---

### Post by monroetransfer on 2007-12-10
I have the same problem. I've toyed around with nearly every option my bios has availed me with, and none have worked. PLEASE can somebody explain how to get out of this, as I've been without a computer to do schoolwork and talk to distant friends and family for weeks. I'm at a public library right now!!!:(:(:(

EDIT: I can't even boot from cd, so now what?

---

