---
title: "Best OS/Distro for SSD? WinXp Win7 Linux"
date: 2011-11-24
forum: Any Other OS
---

### Post by Apv507 on 2011-11-24
I'm planning to get my first Solid State Drive and I'm curious about other people's opinion of the best OS/Distro to run on a SSD. I'm planning on running the drive purely as a boot drive. (I already keep my storage on its own drive). The operating systems I have to choose from are: Windows XP (x64) and Windows 7 (x64) and Ubuntu / any free linux OS out there. The goal of the OS is simple: Let me access the internet, my music, documents and the occasional low resource game while maintaining the life of the drive as best as possible. I want an OS I can install and not have to worry about it senselessly or carelessly wasting disk space.

As far as Windows goes I prefer XP to 7 personally, bud sadly I don't believe XP offers TRIM support and I'd like to keep my SSD clean. Windows 7 does have TRIM support but from what I understand the winsxs file on windows OS'es from vista on seem to grow and grow with no end in sight. My current Win7 has 10.5gbs and 55,000+ files and I don't want that eating up my 60gb SSD.

Based on the above paragraph it seems like a Linux distro is the way to go. I personally prefer Ubuntu from the 9.04 to the 10.10 release. These distro's seems to be lighter and I prefer gnome to unity any day. The 10.04 LTS seems like a good bet. I'm not sure if Ubuntu 10.04 has TRIM support or if I need to enable it. The research I've done made it sound like ext4 was the way to go with SSD's.

Any other thoughts or corrections? Tell me what I missed and point me in the right direction.

---

### Post by wolfen69 on 2011-11-24
I read in a tutorial somewhere that if you choose "use whole disk" during install setup, that alignment is automatic. Below is my fstab from my netbook on a 60gb ssd.


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=26ae869e-0128-4da3-b53e-28d032bcfa62 /               ext4    noatime,discard,data=ordered,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eee1ab9c-a417-4a0f-b35b-8604e36c2185 none            swap    sw              0       0
```

I added noatime and discard myself for trim. Have not had any problems, and the system is VERY fast. I'm running Lubuntu 11.10, but any Ubuntu will do. I can't vouch for any other distro on an ssd, sorry.

---

### Post by Apv507 on 2011-11-25
Hey, thanks for the quick response. I was leaning toward Ubuntu and it sounds like it's the right choice. The programs I (rarely) run on window's will work fun in a virtual machine and VBox always seems to run smoother with a Ubuntu Host. So you say noatime and discard, are they in the repositories? Or are they just lines to add to Fstab? Besides those two is there anything else I could do?  

Thanks again for the help, I've been building computers for almost a decade now and I'm excited to step up to SSD, particularly since the technology has become more accessible as far as price and maintenance go. Btw I love your Gnome 2 Preservation Society link!

Edit: Since I think I'm going with Ubuntu I did a little research, hopefully this will help anyone else in the same situation: 
Ubuntu Distro's and Trim:  [http://askubuntu.com/questions/256/does-ubuntu-have-support-for-the-trim-command-for-use-with-ssd](http://askubuntu.com/questions/256/does-ubuntu-have-support-for-the-trim-command-for-use-with-ssd)
Running Trim: [http://askubuntu.com/questions/18903/how-to-enable-trim/19480#19480](http://askubuntu.com/questions/18903/how-to-enable-trim/19480#19480)

---

### Post by wolfen69 on 2011-11-25
> **Apv507 said:**
> So you say noatime and discard, are they in the repositories? Or are they just lines to add to Fstab? Besides those two is there anything else I could do?  


I just added those 2 things to a line in fstab. Besides those 2 things, there's not much else to do except maybe set your swapiness to a low number. But if you have a lot of ram, that probably won't be necessary. Just add to fstab and you'll be fine.

---

### Post by jimrew111 on 2011-11-25
maybye mint or sabayon?

---

### Post by ojdon on 2011-11-25
> **jimrew111 said:**
> maybye mint or sabayon?

Reason?

I don't think Linux Mint or Sabayon have any sort of SSD optimization.

Personally, I say choose a Linux Distribution you prefer, Apv507 then search Google on how to tune your SSD with Ubuntu to get maximum performance out of it. There are thousands of guides out there. :) 

Also I'd keep away from Gnome2. It's old, sluggish and not in development anymore, there is the MATE project but like the KDE3 fork. I don't think it's going to last very long. Have you tried Xubuntu as a base? It's based on Xfce which is a lightweight Desktop Environment with a similar interface to Gnome 2 and is still maintained frequently. 

Hope this helps!

---

### Post by mips on 2011-11-25
> **Apv507 said:**
> My current Win7 has 10.5gbs and 55,000+ files and I don't want that eating up my 60gb SSD.

Strip Win7 down.
[http://www.hack7mc.com/2010/03/creating-a-windows-7-lite-for-media-center-users-with-vlite.html](http://www.hack7mc.com/2010/03/creating-a-windows-7-lite-for-media-center-users-with-vlite.html)
[http://www.overclockers.com/forums/showthread.php?t=686995](http://www.overclockers.com/forums/showthread.php?t=686995)

---

### Post by Apv507 on 2011-11-25
First, thanks all around for the responses and suggestions, now lets get to it:

> **wolfen69 said:**
> I just added those 2 things to a line in fstab.  Besides those 2 things, there's not much else to do except maybe set  your swapiness to a low number. But if you have a lot of ram, that  probably won't be necessary. Just add to fstab and you'll be  fine.  

 Okay thanks for the help! I have 8gbs of RAM so I haven't needed swap in a while. 

Jimrew111: I used Mint for a while and liked it, but I found I was able to get better performance by starting with Ubuntu and adding the programs I wanted. Mint is great but the last time I tried used it Mint seemed a bit bloated compared to baseline Ubuntu. 

Ojdon: I have used and enjoyed XFCE. It's probably the lightest and easiest out of the box distro I have used and the Xubuntu + Ubuntu Repositories is always a big plus! Am I correct that the 10.04 LTS of Ubuntu will update to gnome 3 with update manager and will that be the same as installing gnome 3 from the beginning? I might end up making a customized installation CD of 11.04 or 11.10 with just gnome and xfce (Unity just doesn't flow for me as intuitively as it does others, I prefer to use my keyboard more than my mouse so gnome-do is much more practical for me, though I will say Unity sure is pretty)

mips: Sorry I meant to say that my winsxs file is 10.5 gigs in my windows installation and as I understand the winsxs file cannot be deleted or trimmed down at all without risking serious complications. My program file and program file (86) folders are only 5.17gbs. Windows is using twice as much hard drive space as I am in that sense and from what I understand winsxs grows perpetually under the assumption that hard drive space will continue to get cheaper or that you'll buy a new computer before it becomes a problem. Both assumptions may be accurate, but a 60gb SSD is a different beast than a 640 gb mechinical drive.

---

### Post by Apv507 on 2011-12-04
Is it safe to dual boot on an SSD? Win7 and Ubuntu 11.10 both have trim or trim like functions. Do SSDs partition well?

---

### Post by mips on 2011-12-05
> **Apv507 said:**
> Is it safe to dual boot on an SSD? Win7 and Ubuntu 11.10 both have trim or trim like functions. Do SSDs partition well?

A SSD behaves just like a normal HDD, you can partition, dual/triple/quad etc boot to your hearts content!

NOTE: Do NOT create a SWAP file/partition on your SSD (for any OS), rather put it on a normal HDD.

---

### Post by wolfen69 on 2011-12-05
> **Apv507 said:**
> Is it safe to dual boot on an SSD? 
There's no reason it wouldn't be safe.
> Win7 and Ubuntu 11.10 both have trim or trim like functions. Do SSDs partition well?

Same as any other drive.

---

### Post by Apv507 on 2011-12-05
> **mips said:**
> A SSD behaves just like a normal HDD, you can partition, dual/triple/quad etc boot to your hearts content!

NOTE: Do NOT create a SWAP file/partition on your SSD (for any OS), rather put it on a normal HDD.

Okay thanks! I have 8gigs of ram so I haven't need swap in while. I figured SSD would behave like a HDD but I guess I've bought into the hype that SSD's are fragile and temperamental, despite the fact that most of them have over 10 times the MTBF of most PSU's and I've never had a PSU fail on me. 

Thanks for all the help the SSD should be here in the next two days, so hopefully by then I'll have made up my mind on what I want to do.

---

### Post by Apv507 on 2011-12-06
I'm currently dual booting Win7 and Ubuntu 11.10 and boy is it fast!. The Windows logo doesn't have time to form fully before the screen flashes and my desktop is fully loaded. Thanks for all the help, here is a good Windows 7 SSD optimization guide I found too:

[http://www.speedguide.net/articles/ssd-speed-tweaks-3319](http://www.speedguide.net/articles/ssd-speed-tweaks-3319)

(I don't like to ask questions without doing some research myself, seems lazy)

I doubt anyone that posted on this thread needs that link, but maybe they will pass it on.

Thanks again for all the help and happy holidays,

Apv

---

### Post by mips on 2011-12-07
Guides for linux,
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://opentechnow.blogspot.com/2010/02/linux-ssd-optimization-guide.html](http://opentechnow.blogspot.com/2010/02/linux-ssd-optimization-guide.html)
[http://grzen.blogspot.com/2009/05/ssd-optimization-on-linux_18.html](http://grzen.blogspot.com/2009/05/ssd-optimization-on-linux_18.html)
[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

---

### Post by Apv507 on 2011-12-07
Thanks Mips, you've been a great help. IMO this is not only solved but a great guide for people interested in maintaining their SSDs.

---

### Post by Basher101 on 2011-12-07
Here is a really great website i found after some hours of googeling for SSDs. It is about how you get the maximum Lifetime out of your SSD, in other words minimizing all Writes to the SSD. Hope it will help: 

[http://blog.superuser.com/2011/05/10/maximizing-the-lifetime-of-your-ssd/](http://blog.superuser.com/2011/05/10/maximizing-the-lifetime-of-your-ssd/)


regards

---

### Post by Apv507 on 2011-12-07
> **wolfen69 said:**
> I read in a tutorial somewhere that if you choose "use whole disk" during install setup, that alignment is automatic. Below is my fstab from my netbook on a 60gb ssd.


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=26ae869e-0128-4da3-b53e-28d032bcfa62 /               ext4    noatime,discard,data=ordered,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eee1ab9c-a417-4a0f-b35b-8604e36c2185 none            swap    sw              0       0
```I added noatime and discard myself for trim. Have not had any problems, and the system is VERY fast. I'm running Lubuntu 11.10, but any Ubuntu will do. I can't vouch for any other distro on an ssd, sorry.


Hey, other guides I've found indicate that the noatime and discard options should be added under the <options> column, not the <pass> column as is done here, can anyone confirm either way?

*EDIT*  MY mistake, it is in the option column.

---

### Post by Apv507 on 2011-12-08
Another helpful hint to minimize writes: avoid proprietary drivers and unity, because they tend to be buggy and removing them prevents unity from loading. Using CCSM to enabling unity doesn't work, in fact the only thing that does work is reinstalling the buggy driver. Looks like I'll be installing Ubuntu for the Nth time on this SSD. Wish I'd figured out that it was this driver causing the problem earlier on. I thought it was some upgrade or the fact that I installed gnome and xfce, but alas after two days of reinstalling and reinstalling I finally found the rotten little culprit.

---

