---
title: "Help a Linux Beginner, please?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by xAix on 2005-12-07
Hi. So I just recieved my ShipIt CDs in the mail a while back, and I tried installing Ubuntu 5.04 on my computer, although I'm a total newbie at this. So I tried to install it [using some tutorial I found off the internet](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/), and, long story short, it wouldn't boot. I followed the guide to a T, partitioning my hard disk as such:
[img]http://img15.imgspot.com/u/05/340/03/part1133942494.JPG[/img]

So I got my ubuntu.bin file off using the Live CD (mounting my hard drives using that and doing what was in the tutorial--using the Live CD instead of the recovery disk suggested), and when I boot up, I get a "GRUB Geom Error." I'm pretty sure that I got everything right (even did it two times), I already installed the base system; my problem is that it would not boot. I'm suspecting that it was because of how I partitioned my HD, since it "crosses the 1024 cylinder boundary" according to PartitionMagic, but even so, my BIOS supports LBA. What seems to be the problem? What other solutions could you people offer for booting?

BTW, I almost forgot--I'm dual-booting it with Windows XP and I can't install it to my other HD/partitions since I don't want to mess with the files there.

Many thanks!:)

---

### Post by aysiu on 2005-12-07
[QUOTE=xAix]So I tried to install it [using some tutorial I found off the internet](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/), and, long story short, it wouldn't boot. I followed the guide to a T[/QUOTE] I'm sorry you found that tutorial and not [this one](http://users.bigpond.net.au/hermanzone/).

---

### Post by KermitJr on 2005-12-07
Well, nothing against Matthew, but just go ahead an install it to the Master Boot Record (The GRUB Default).  It will automatically make a Windows entry for you.  This is what I have done on all my machines without issue (Win98/XP/NT/2k).

Try that once and you should be good. (Just delete the linux partition from inside the Ubuntu installer and have it use free space.)

Hope this helps,
KJ

---

### Post by aysiu on 2005-12-07
[QUOTE=KermitJr]just go ahead an install it to the Master Boot Record (The GRUB Default).  I will automatically make a Windows entry for you.  This is what I have done on all my machines without issue (Win98/XP/NT/2k).[/QUOTE] Likewise, for me.

---

### Post by xAix on 2005-12-07
Thanks, aysiu, I'll check out that tutorial. Looks good to me.

I already tried installing GRUB to the MBR, but I always get "GRUB Error 17" upon boot, can anyone explain why? And are there other boot managers available? I tried LILO, and it won't work either on the Linux Partition or the MBR.

Thanks everyone!:D

---

### Post by aysiu on 2005-12-07
[QUOTE=xAix]
I already tried installing GRUB to the MBR, but I always get "GRUB Error 17" upon boot, can anyone explain why?[/QUOTE] I've never experienced this "error 17," but [other people here have](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+GRUB+Error+17&btnG=Google+Search).

---

### Post by xAix on 2005-12-07
Hmm, weird. Error 17 seems to point to invalid/unrecognizable filesystems, as I understand. Maybe a little more details would be helpful. I have two hard drives, one a Western Digital 160GB one, which I have partitioned as shown above, and installed linux on a Ext3 partition (BTW, is Ext3 better than Ext2 when it comes to performance?). So there. 

Again aysiu, thanks for the response.

*edit* [This post](http://ubuntuforums.org/archive/index.php/t-81593.html) seems to point out that the boot/Linux partition can't be put past the 1024 cylinder boundary. Is this correct? So I'll have to install Linux on yet another HD because of this?

---

### Post by xAix on 2005-12-07
Sorry for the double-post, but I had to bring this thread up. Seems like I screwed-up my MBR once again (thanks to GRUB probably not being too friendly with my bootsector), and I got "Missing Operating System" when I tried to boot up to Windows. I already tried FIXMBR from the XP Recovery Console, nothing. :(

---

### Post by timsch75 on 2005-12-07
You do not need a new HD to use Linux.  I have mine installed at the end of an 80G HD.  the /boot does need to be installed in the first 1024 cylinders (1.7 cylinders/meg), but your installation should take care of this unless you specifically instructed it to install /boot somewhere, which is unlikely.  It's no surprise that the XP recovery was ineffective.  Windows doesn't deal as well with Linux as Linux does with windows.  I wish I could be more help.  I'd try a new install using a burned set of the new Breezy 5.10, use the recommended tutorial, and install to the MBR.  I did this the other night with win2k and it worked great

---

