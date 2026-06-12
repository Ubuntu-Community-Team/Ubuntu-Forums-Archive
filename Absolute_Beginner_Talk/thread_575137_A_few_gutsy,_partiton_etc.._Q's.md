---
title: "A few gutsy, partiton etc.. Q's"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-13
OK, a few questions, I plan ahead soo..... it might be a little early to ask.

1. I shall do a clean install, now please give some advice on partitioning (i heard alot of them). Should I do a /home /boot and / and swap partitions differently?
2. Any idea how big is gutsy (praying its less then 800Mb)
3. If I clean install, compiz fusion is going to be included do I still want beryl?
4. Is all the drivers in feisty included in Gutsy?

Also as a side question

Why can't I partition using Gparted in the live CD? there are little locks around and when I click properties it says "unable to find mount point" at the bottom, Should I just the the hell over with windows (delete it all) and have a ubuntu only computer?

And will the MBR be messed up because of the new GRUB and the old one colliding maybe?

If I want to get over with windows is there anything that can run maplestory (maplestory.com) in ubuntu? *wine doesn't work because of game guard*

Thanks~
:popcorn:

---

### Post by Pumalite on 2007-10-13
Get rid of Windows and use Gparted Live CD to partition your drive. A good scheme is:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for home.
Then install. Gutsy comes with drivers for Nvidia and ATI
Size is 694 MB aprox

---

### Post by InsertNameHere on 2007-10-13
No intel?

Is there other emulators that run maplestory? other then vmware (I don't feel good giving personal info).

---

### Post by defrex on 2007-10-13
If you're giving the whole drive to Ubuntu, it wouldn't be a problem to just have two partition (/ and swap). Personally, however, I put /home on it's own partition. This way is I manage to screw my system badly enough (and I always do eventually) I can reinstall without losing my home directory (and thus all my personal data and app settings).

My current Gutsy install (which has a few extra things installed) takes up about 5.5G. That's not including /home (which is 100s of gigs for me).

Compiz Fusion is the new Beryl.

There will be more drivers in Gutsy, rather then less. 

I have no idea why Gparted doesn't work.

Don't worry about Grub, it'll take care of itself. The installer will detect anything bootable on the drive and add it.

As for running a windows app without Wine: *virtualization* is your new best friend. Google vmware or virtualbox.

---

### Post by Pumalite on 2007-10-13
It comes with 915resolution.

---

### Post by InsertNameHere on 2007-10-13
Will I be able to use the installer (manual partition thing) to resize my partitions, if Gparted doesn't work.

And my internets slow so I don't download stuff, I given myself a excuse to download gutsy, and I finally have a excuse to switch to KDE.

a few questions

Is KDE really that SLOW?
Does KDE look better then gnome? (critical)
And does KDE really have more control?

As I said I donot want vmware because it asks me personal info, but does virtual box work with INCA (nProtect) game guard? (Maplestory specifically)

Thanks for all the useful replies.

---

