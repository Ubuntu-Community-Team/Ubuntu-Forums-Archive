---
title: "MBR Questions"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-06-26
Hello. I started with a Windows system, and added a second drive with my Ubuntu partitions. The Win drive came with a "safety" partition, which takes up the first 16 Gigs of that drive. Because of the size, I assume the MBR is in there. I installed GRUB into my MBR. I want to nix the Windows, as I haven't booted into it for months. I don't want to get into changing the drive IDs and all. My idea is to take my high-speed drive out of the closet, copy the "safety" partition onto the new drive, and use the rest of that drive for media.. I know there are a few complications involved in all of that, but right now my concern is this: Is the MBR in that "safety" partition?  If so, will keeping that and just deleting the Windows partition cause any problems with my boot, or is everything self-contained in that MBR and the /boot directory of my Ubuntu partition? 

Thank you for your help.

---

### Post by Rui Pais on 2007-06-26
Hi.
No, the MBR is a special zone at the beginning of your HD, the 1st. sector (512bytes) of the disc. 
It's not inside any partition. Delete a partition will not delete/remove MBR.
You can use a tool from Linux to backup and/or copy it:

backup (for this example i use sda):
```
dd if=/dev/sda of=sda.mbr.backup bs=512 count=1
```

copy backup to MBR: 
```
dd if=sda.mbr.backup of=/dev/sda bs=512 count=1
```

hth

---

### Post by coldstatue on 2007-06-28
ok, cool. So where will it back up to? Iit would be great if I could plug in a 3rd drive (sdc), copy it to that, then, remove sda, and make the 3rd drive the new sda - never having to use a live cd or anything. my current sda is a slow old drive, and these 10k drives are really nice.

---

### Post by Rui Pais on 2007-06-28
> **coldstatue said:**
> ok, cool. So where will it back up to?
hi.
Where you want it :) 
It will backup as file, so you save it where you like (even on a USB stick... it's just 512b long). 
In my example, above, it should be saved at the home directory of the user.
Note that it's just a precaution. In years of "wild" use with computers i never reput a mbr backup. Not a single time.

At most you may broke grub booter MBR (not by deleting the Window partition, anyway)
A more useful tip is now how to reinstall grub on MBR:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
and
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

>  Iit would be great if I could plug in a 3rd drive (sdc), copy it to that, then, remove sda, and make the 3rd drive the new sda - never having to use a live cd or anything. my current sda is a slow old drive, and these 10k drives are really nice.

Well this is Linux, we have a lot of rabbits in our hats ;)
Since you have only one Linux installed, and it's not a great idea copy a live OSs, the better option would be boot from a liveCD, but just copy your Ubuntu Installation. 
No need to reinstall or reconfigure.
Is a simple task but can look hard if you are not used to Linux commands/concepts.

If you want to try i can post some basic instructions... 
As long as you don't write nothing on sda during the copy process, it's safe. 
And the worst that can happen it's fail to boot from new sda (the duplicated) making you go back to your actual one.

---

### Post by coldstatue on 2007-06-28
Well, my linux install is on a high-speed *sdb.* I'm not sure I understood you / explained myself well. I just want to get rid of sda, (slow win drive) but keep sdb as sdb. Then, put the new high-speed sda in, copy the MBR to it, and use that one for boot, even though it will be a media drive. Oh, I also have Ubuntu Studio installed on another partition of sdb, but I have a feeling the reason you didn't want me doing this with a live OS is because you thought I was copying my operating system, right? I just need to copy the MBR, but it is kind of complicated. If I have enough plugs in my comp, I will just have all 3 drives in at once, and copy the MBR to #3. Then, I can just unplug #1, change some jumpers, and test if it boots. So, when I run the command you gave, it will ask me for a save location?

Thank you so much for your help. You rock.

---

### Post by Rui Pais on 2007-06-28
Oh sorry, i didn't understand exactly what you wanted at first.

Ok, then its easier. You just need to install grub boot loader to the new SATA. 
I assume your boot partition(s) is on sdb, is that correct?

Just plugin your new HD (the future sda) and boot to one of your Linuxs. 

Ensure that it has been detected as sdc (use something like fdisk, cfdisk or gparted). 
If it's ok then, on a terminal run:
```
sudo grub
```
then it will lead you to grub shell (it says 'grub>') Now type:
```
setup (hd2)
```
and exit by typing 
```
quit
```
thats all. 

Now power off remove/unplug old sda. Set the new one as sda, and should be booting normally.

If something goes wrong, it's just a question of put back old sda and post what was the error output (or what happen). Should be no problem...

Good luck.

---

### Post by coldstatue on 2007-06-28
so it will copy all of my settings over?

---

### Post by Rui Pais on 2007-06-28
> **coldstatue said:**
> so it will copy all of my settings over?

No. Your settings are inside /boot/ partition. They are already set and will not be touched.
The MBR is a special part of the disc. What you save there is only a "flag" that make it boot (see [here]("http://en.wikipedia.org/wiki/Master_boot_record") for general info).

I'm not sure if you need to pass too the location of boot partition. 
I think it's not needed but won't hurt, so you can do, before the setup (hd2): 
```
root (hd1,N) 
```
where N is the number-1 where your boot partition is (if it's on sdb2, e.g., would be root(hd1,1)...) 
and then:
```
setup (hd2)
```


Yet another way of do it, maybe more clean and direct, would be:
turn power off, unplug the actual sda, plug the new drive to be sda. 
Boot from a live cd and follow the [usual procedure to recover grub here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Here a thread too with some tips:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by bodhi.zazen on 2007-06-28
Yes it will, but you need to tell grub where to copy the settings from.

do this by identifying root :

Root is the partition with your current /boot/grub/menu.lst ; the one with the current settings you want to copy, but in grub speak. Linux = /dev/hdxy Grub = (hdx,y)

> sudo grub

grub> root (hd0,0)
grub> setup (hd1)
grub> quit

But you need to know your partitions in grub speak. In grub nubmers start with 0. so first HD = 0, second HD =1

First partition =0, first partition on first HD = 0,0 ...

get it ? If not : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Rui Pais on 2007-06-28
hi bodhi.zazen,
the problem is that coldstatue have grub on MBR of 1st HD and /boot on 2nd HD  and want to save grub loader on a 3rd HD to replace the first...

---

### Post by bodhi.zazen on 2007-06-28
Well, one has to position the hd first, then reinstall grub into the mbr of the (first) boot drive.

---

### Post by coldstatue on 2007-06-29
Thank you all. This is great info. It is not easy to find the  specific  details for my particular situation.  As always, this community comes through with years of expertise and results I wouldn't expect when paying for support for another OS. Even in comparison with every other open source forum I've seen, it's clear that something great is happening here.

I'd better go before I start saying" I love you, man!", blubbering and crying all over the place.
 

Many thanks.

---

