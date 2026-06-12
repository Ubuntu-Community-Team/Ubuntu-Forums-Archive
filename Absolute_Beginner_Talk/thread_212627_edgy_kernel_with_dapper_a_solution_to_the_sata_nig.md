---
title: "edgy kernel with dapper a solution to the sata nightmare?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by ronly on 2006-07-10
Hi all!

I've read a lot on the forums and it seems pretty clear to me that there's simply no way I can get the current dapper kernel to work with my sata harddrive to work with my nforce4 (Asus K8N4-E Deluxe) motherboard. So now I'm wondering how I should get my system usable again and have a few questions:

Being a newbie I made the stupid mistake of just changing breezy to dapper in sources.list and then running upgrade. What problems can that cause? I did run aptitude dist-upgrade afterwards but don't know whether that did anything useful. I had a few problems with breezy and many of those seem to be fixed in dapper so I'd really like to run that (among other things alsa didn't work very well with my sound card and a known issue was that my graphics card required a newer nvidia driver than the one in breezy). Would a dist-upgrade after installing breezy again result in a much better system?

My current system is badly broken but I can run it if I choose the old kernel in grub but most modules aren't loaded then (I have to modprobe the ones required by my dvd drive, sound card and dvb card manually). Is this due to the system being otherwise upgraded but the kernel still being the old one?

Running the dapper kernel is simply impossible due to the numerous problems with it - I believe that many of you know that not even installation is possible without some tricks since sata harddrives don't show up and I'm a little bit unsure whether I should even try it even if I could make it detect them using the tricks suggested since I fear that I might end up with an even more broken system (I've read about the problems with installations that never finish). Would reinstalling breezy and then dist-upgrade to dapper and manually installing the edgy kernel deb + modules + headers result in a good system (assuming that the sata drive problem has been solved in that kernel) or would that be impossible? My impression is that that would be the best solution in my case since the dapper kernel doesn't work but dapper seems to be otherwise better but I'd like to have some experienced users comment before I try that.

If anybody knows whether a fixed version of dapper is about to be released shortly I'd obviously like to know that since in that case I could wait for that and withstand my current badly broken system for a few more days.

---

### Post by keith whitehouse on 2006-07-10
hi ronly,

I have read your post a few times and I keep coming back to sata drives, and I am a bit confused.

I have 2 hards drives both sata. The larger one is in fact 10 seperate drives made under Hyperos and all running their own operating system and their own programs. The 80 gig drive (drive 2) I partitioned using gparted and then installed Ubuntu on it. It has / home and swap. I have Dapper Drake fully upgraded and it runs fine. I dont seem to remember having any trouble at all installing anything on it. Before I put Ubuntu on it, it was in 2 partitions, the first was just a data partition, and the second half was for dragging copies of important files to every day from the main drive.

All drives and partitions were originally fat32

best regards keith

---

### Post by ronly on 2006-07-10
Thanks for your reply, I should probably elaborate: The problem I'm referring to is what e.g. ubuntu_demon referred to as the "Worst bug in Dapper" in his blog. Many users have the same problem that sata drives and nforce4 chipsets (and possibly others) result in no /dev/sd* being found - so simply booting the installation cd requires some tricks if you want it to find the hd and it's uncertain whether installation is possible that way. In my case I've unfortunately tried to upgrade a breezy installation and ended up with a very broken system that I can run using an older kernel but get many, many problems with that and am stuck now not knowing whether it would be worth the trouble to reinstall breezy even though I'd like to upgrade to dapper due to other improvements or if I should try to repair my current system or find some other way to run dapper - I've read all the tips in the threads linked to [here](http://ubuntuforums.org/showthread.php?t=187656) under "booting stalls during "mounting root filesystem"?" but nothing has helped :( I have contemplated compiling a new kernel myself (the latest vanilla, probably) to see if that would work.

---

### Post by keith whitehouse on 2006-07-10
hi ronly,

I have just read the 16 pages that you refer to, and I would not be convinced that it was all down to sata drives. Everything is mentioned ranging from sata drives to usb to disc writing and disc players etc. It would appear at the moment that there are a large number of solutions being offered. I am not even sure if everybody has the same problem as there appears to be a lot of confusion when people try to explain their own personal circumstances.

I hope that you manage to resolve the issue at some stage

best regards keith

---

### Post by tassou on 2006-07-22
NOT SOLVED IN EDGY KNOT1 !

Booting the iso, looking for hard drive discs in /dev : nothing !
Initiating the installation process : Gparted fails to find any HDD !
Very critical, I'm still under Breezy, unable to upgrade to Dapper, and Edgy seems to have the same problem.

---

