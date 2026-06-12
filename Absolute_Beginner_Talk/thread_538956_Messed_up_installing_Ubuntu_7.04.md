---
title: "Messed up installing Ubuntu 7.04"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Joe1234 on 2007-08-30
Hi all,

I installed Feisty Fawn a few weeks ago, and I really love it.  However, I messed up when I installed it. I had XP on my laptop, and I wanted to partition the hard drive and be able to dual-boot XP and Ubuntu.  I used the CD to install, but for some reason the automatic partition option would lead to the computer freezing. I thought that I understood enough to do manual partitioning (dumb!), so I tried that instead.  I have an 80 gig hard drive, so I made three partitions: one with 20 gig and ext3 (/), one with 512 mb and ext2 (/boot), and one swap (1 gig). I then went ahead with installation and everything worked fine. I used Gnome partition editor, and this is what my hard drive looks 

[http://img404.imageshack.us/my.php?image=partitionsrs3.png](http://img404.imageshack.us/my.php?image=partitionsrs3.png)

Now, however, I realized that I did not make a partition for Windows, and can only boot with Ubuntu. 

My question is this: First, is there any way to save XP with all the files and programs that I was using before? I backed up the important files, but I would still like it if I could get everything I had before back. I know this is unlikely, but it says the space is unallocated, not deleted, right?

Second, if it's not possible to recover any files destroyed by my dumb mistake, how do I re-install XP in the unallocated partition? I still really want to be able to dual-boot, but I have no idea how to do it from Ubuntu.

Thank you very much for your help!

---

### Post by eapache on 2007-08-30
It may be possible to recover XP, but only with a professional (and very expensive) data recovery tool. Since you have your important data backed up, I would suggest reinstalling.

It is possible to reinstall in the unallocated space, however you will need to tinker with your grub to get dual-boot working. Your best bet is to back up any important stuff you have on ubuntu and reinstall Windows fresh on the whole drive (wiping Ubuntu). Then re-install ubuntu (no licensing means you can do this unlimited number of times if it doesn't work). After you reinstall XP, I will provide a detailed walkthrough on installing Ubuntu beside windows.

EDIT: Why did you include a separate boot partition? That gets pretty advanced, and I wouldn't have suggested it for someone with your level of experience.

---

### Post by jingo811 on 2007-08-30
Yeah that /boot partition looked weird I've never seen anybody use it or mention it in real life situations.
Your problem sounds like a mess.  If you have Windows XP full installation CD then.....

save yourself some headaches and prepare for a complete FORMAT C:\ and delete everything on your Harddrive.  Installing full Windows XP from scratch first and then Ubuntu will be easiest.

[SIZE="4"]If you don't have Windows XP full installation CD then don't listen to me[/SIZE] :)
[COLOR="Red"]but do backup exactly every piece of personal data you can think of in either case![/COLOR]

---

### Post by eapache on 2007-08-31
The only reason I can think of to have a separate boot partition is if you want to encrypt the rest of the disk, but that gets really complicated.

---

