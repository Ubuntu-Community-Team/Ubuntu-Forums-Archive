---
title: "creating a separate /boot partition for multiboot"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by hmspharm on 2007-09-08
Okay, I checked out the threads, they've got good info for future reference, the problem is I'm a complete noob and I've already installed 2 distros on 2 separate partitions, and I want to uninstall the most recent one and keep the original distro, preferably without messing up GRUB. Most of the advice I've found so far concerns creating a separate /boot (or /home, etc.) partition during the original linux install. Found this quote from matthewv while browsing: "All you need to do is run 'sudo grub-install hd0' from the ubuntu install you wish to keep. This will rewrite the grub install in the boot sector with one that points to the partition of the ubuntu you wish to keep." HymnToLife wrote: "And next time, if you want to install more than one Linux distro, remember to create a separate /boot partition to use with all of them, it makes muti-booting way easier"  Okay, I can handle the first part, anybody got any suggestions for doing the second without starting over and re-installing from scratch?

Thanx in advance,
hmspharm

P.S: the distros are linux mint 3.0 gnome (original) and linux mint 3.0 kde edition. I like gnome better so I want to lose the kde version, maybe try something else later; since mint seems to be 99% ubuntu, next one I try will very likely be Feisty (or Gutsy).

P.P.S: lots more info here than on mint forums, that's why I'm here :)

---

### Post by logos34 on 2007-09-08
-Run grub-install to reinstall grub pointing to the linux mint 3.0 gnome (original). 
-Use gparted to delete the kde partition...in the empty space create a small new ext3 /boot, with the rest of the space left for whatever distro(s) you decide to install.  

At this point you have 3 primary partitions (Mint root, swap, /boot).  One more and that's the limit.  So you might consider creating an extended out of the remaining disk space, which can be subdivided up into many logical partitions.  You could even have done this before creating /boot, and put it inside as a logical).

-Try the following howto for moving boot folder to dedicated partition:

[http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/](http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/)

when you're satisfied everything is in order and works, delete the 'oldboot' folder.

Note: the part about '/boot/xxx.x' refers to these lines:

> kernel	       /boot/vmlinuz-2.6.20-16-generic...
initrd		/boot/initrd.img-2.6.20-16-generic...

Don't forget to change the 'kopt=root=' and 'groot=' lines

Hopefully that should do it.

---

### Post by hmspharm on 2007-09-08
I really appreciate the info, logos34, it'll save me much grief in the future!
Thank you very much:)
hmspharm

---

### Post by hmspharm on 2007-09-09
:confused:I'd really like to do this one step at a time, i.e., get rid of the kde partition, then worry about creating a separate boot partition later. I've done as you suggested and re-installed grub with it pointing to my original partition, first from inside gnome mint, then from inside kde mint, and nothing seems to change: menu.lst hasn't changed in either partition, both /boot/grub folders contain stage 1.5 and stage 2 files, and every time I reboot I get the same grub choices (kde listings, then Windoze, then my original gnome choices). More detail: originally I had one hd with XP installed, then I added 2nd hd, divided it into 3 or 4 fat32 partitions, and installed mint on one of those (hd1,9), then later installed kde mint on hd1,11 (or sdb12). I'm assuming that stage 1 of grub is installed in mbr of hd0, and it still points to stage 2 on kde partition, which is why nothing seems to be changing. I'm worried that if I just go ahead and delete the kde install, I'll have an unbootable system, unless grub automatically searches all the hard disks until it finds stage 2. I'm trying to understand exactly how grub works, but the more I read the more confused I get. For me it's kind of like which comes first, the chicken or the egg? Should I be doing everything inside gnome or kde partition, should I be deleting an installation and then reconfigure grub, or vice-versa, etc.? I'm tempted just to reinstall gnome mint over the kde install, then move my home folder, or install ubuntu on top of kde gnome, but I was hoping there was a more simple and elegant solution. I'm a total noob at this stuff so please bear with me, but I do feel like I need a specific step-by-step how-to in words of one syllable or less!:)

Thanx again,
hmspharm

---

### Post by hmspharm on 2007-09-09
Doh!... just realized I need to grub-install hd0, not hd1... did that, got everything back to where it was before, next I'll attempt to set up the separate /boot partition... man, I sure do make things more difficult than I need to, sometimes! So disregard previous reply, I'm getting it figured out, albeit slowly....:)

Thanks again for your patience,
hmspharm

---

### Post by logos34 on 2007-09-09
I was just about to ask you for your fdisk -l because that's the first mention I've heard about a 2nd hard drive...yeah, hd0 is what you wanted...grub (the tiny 512 byte stage1 file) installs by default to the first Bios hard disk (i.e. hd0) even though the linux root is on a different disk (in this case hd1, but it could be hd2, 3, and so on).  That's waht confuses everyone, they always think it should be on the mbr of the same disk.  So basically grub stage1 just points to the root (or /boot if on a separate partition) and hands off the boot process to stage2 which knows where to find the kernel images.

---

### Post by logos34 on 2007-09-09
just for future reference:

instead of 'grub-install hdx' or 'grub-install /dev/hdx' method, it's better do it this way:

> sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)  

The reason being that it's easy to see where the root partitions are and harder to make a mistake.

---

### Post by hmspharm on 2007-09-09
Sorry about that, I had been posting messages on the mint forums for a while before I hopped over here, was getting tired and lazy so I left out too many details originally. Anyhow, since my last post I've tried moving the boot partition according to directions on the site you suggested, ended up with a grub> prompt, had to type parameters in manually to boot up. Good thing I didn't delete "oldboot" folder, was able to get back to where I started fairly easily. I'm either missing something very obvious or I'm just too inexperienced to fill in the gaps in the instructions (if there are any). Remember, I'm still at the stage where I pretty much need every step spelled out in excruciating detail, but I'm hoping to get past that point reasonably quickly if I just keep plugging away at it.:)
At least now I know how to edit menu.lst and reinstall grub so it points to the distro I want it to, if I do keep playing with other distros. I don't know if I'll take another stab at the separate boot partition, or wait to see what kind of gui front ends for bootloaders might be coming out in the near future.

Anyhow, I really appreciate all the help, and, even though I'm a slow learner, I am making progress, even if it is in fits and starts!

Thanks again,:)
hmspharm

---

### Post by logos34 on 2007-09-09
Did you use **sudo** with the commands and substitute your drive '**[COLOR="Blue"]sdb[/COLOR]X**' for all instances of 'hdaX'? (assuming you created the new /boot on sdb disk)

And for the grub-install line, you should have used

**sudo grub-install /dev/[COLOR="Red"]sda[/COLOR]**

OR

**sudo grub-install hd0**

It's also possible a typo creeped in somewhere while changing the 'root' lines in menu.lst. 

kerenel and initrd should have been edited to look like this:
> kernel /vmlinuz-2.6.20-16-generic...
initrd /initrd.img-2.6.20-16-generic...

---

### Post by hmspharm on 2007-09-09
I used sudo for everything, sdb13 for "hdax", sudo grub-install /dev/sdb13, and on the kernel and initrd lines I changed /boot/vmlinuz-2.6.20-16-generic... to /vmlinuz-2.6.20-16-generic..., and /boot/initrd.img-2.6.20-16-generic... to /initrd.img-2.6.20-16-generic... also did changes to groot and kopt... followed example for kopt first time so I ended up with something like: kopt=root=/dev/sdb13 ro, when that didn't work I chaged it back to original: kopt=root=UUID=29c0a893-0d16-4724-af31-746aa5b44518 ro, but it still didn't work.

Hmmm....I wonder if kopt should have been pointing to /dev/sdb9, since that's where my gnome mint install actually lives? but then what's the diff between that and the UUID above?

I think I'm in a little bit over my head. I downloaded the super grub disk .iso, but haven't burned a cd yet. Maybe I better leave well enuf alone, eh?

Well, I guess that's all for now...
hmspharm

---

### Post by logos34 on 2007-09-09
First, please post your fdisk:

**sudo fdisk -l** (lowercase L)

If you're still booting to the first disk, sda, then you wanted to run

sudo grub-install /dev/sda

or

sudo grub-install hd0

This writes it to the mbr, pointing to the new location of /boot at sdb13 (i.e. hd1,12).

 'sudo grub-install /dev/sdb13' installed it to the bootsector of the new /boot partition. 

'kopt' and 'groot' in your case need to point to /boot rather than /.  That UUID is for your root, so you can't use that one.  If you want to use the UUID for /boot instead of '/dev/sdb13' format then check it with 

**blkid**

or 
[B]
ls -l /dev/disk/by-uuid[/B]

---

### Post by hmspharm on 2007-09-09
Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2        4178    33551721    b  W95 FAT32
/dev/sdb6            4179        8355    33551721    b  W95 FAT32
/dev/sdb7            8356       10299    15615148+   b  W95 FAT32
/dev/sdb8           12533       14476    15615148+   b  W95 FAT32
/dev/sdb9           16710       19457    22073278+   b  W95 FAT32
/dev/sdb10  *       14477       16610    17141323+  83  Linux
/dev/sdb11          16611       16709      795186   82  Linux swap / Solaris
/dev/sdb12          10300       12519    17832118+  83  Linux

Partition table entries are not in disk order

Okay, this is the part that confuses me: "Note that you also need to change /boot/xxx.x entries to /xxx.x since the /boot partition is itself the root path for grub." That's why I was deleting the /boot in the menu.lst lines. BTW, I've already deleted sdb13, as you can see.

Thanks for sticking with me, I really appreciate it!:)
hmspharm

P.S: sdb12 used to be kde partition, sdb13 was the swap partition, now it's unassigned.

---

### Post by logos34 on 2007-09-10
The part about 'boot/xxx.x' -->'/xxx.x' just means that when you move everything to the new /boot, because /boot is itself a separate partition and not a directory within the root partition, it effectively becomes root as far as grub is concerned.  So kopt, groot and root lines should all point to the boot partition.

If you feel like it, try it again but this time make sure to write grub to the mbr of sda and not anywhere on sdb, because you're not booting to that disk.

---

### Post by hmspharm on 2007-09-10
Thanks, I probably will try again pretty soon, but next time I'll make sure I'm better prepared, have plenty of sleep and a lot of time to work with it, just in case!

Again, thank you very much for all your help:)
hmspharm

---

