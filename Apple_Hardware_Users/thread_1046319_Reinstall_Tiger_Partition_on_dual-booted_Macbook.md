---
title: "Reinstall Tiger Partition on dual-booted Macbook"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by BuffaloBill on 2009-01-21
Hi!

I am really sorry if someone already posted on this subject, but I tried really hard to find it in the forums before asking.

Here's my problem:

I want to reinstall only the Mac partition on my MacBook as my Linux works perfectly and I don't want to reconfigure everything.

I was still using my Mac partition because... I play WoW -_-... But I got my account stolen and the only way that this would have been possible (imho) is a keylogger (ok, that's unusual even for a Mac).

So, not feeling secure even with 2 scans from different anti-spyware and anti-virus, I would like to wipe off the Tiger partition and reinstall it so I could continue using my Ubuntu partition for my homeworks!

Thanks guys!

I have a Macbook (2,1) 2,16 GHzIntel Core 2 Duo

---

### Post by BuffaloBill on 2009-01-21
I may be not clear enough.  I just don't know if installing my Mac partition will damage my Linux one.  Anybody went through this process before?

I'm not a total nub with computers but I must say that dual boots are new to me and I never encountered any major problems before.

Thanks!

---

### Post by cyberdork33 on 2009-01-21
1. Boot from the OSX installation DVD and start Disk Utility from the menus.
2. Select your OSXVolume on the left side (Not the top level, whole disk, the one that should be named "Macintosh HD" unless you renamed it.)
3. Click on the "Erase" tab.
4. Select "Mac OS Extended (Journaled)" as the Volume Format.
5. Name your disk what you want (default is "Macintosh HD")
6. Click the "Security Options..." Button and in the popup, choose to "Zero-Out Data". (You can choose 7-Pass Erase if you are paranoid, or 35-Pass if you are super paranoid... 35 is just overkill.) Click OK.
7. Back in the Erase Tab again, Click the "Erase" button to apply the options you chose.

When this is done you will have a completely blank OSX partition which you can start the installation of OSX onto after you quit Disk Utility.

---

### Post by BuffaloBill on 2009-01-21
Thanks a lot!  This would not affect my actual Linux partition?  

I mean, I have been using Ubuntu for quite a long time now and its running perfectly.  I use reFFit and I got some pretty important stuff on it! I'll make a backup disk anyway!

---

### Post by cyberdork33 on 2009-01-21
> **BuffaloBill said:**
> Thanks a lot!  This would not affect my actual Linux partition?  

I mean, I have been using Ubuntu for quite a long time now and its running perfectly.  I use reFFit and I got some pretty important stuff on it! I'll make a backup disk anyway!

You will have to reinstall rEFIt, of course, and could possibly need to resync the partition tables, but that should be all.

---

### Post by BuffaloBill on 2009-01-21
Ok, did the reinstall with the Mac disk and got rEFIt on.  Now, it seems it can't find the boot part.  How can I fix that?

---

### Post by BuffaloBill on 2009-01-21
I'm trying to find something about resyncing the partition tables on Google and the forum but can't seem to find the appropriate topic :S

---

### Post by BuffaloBill on 2009-01-21
Hmm I see a slight problem.  I did the sync (almost by mistake!) and the tables are "sync" as the tool tells me.  Problem is, the Linux icon appears and then nothing.  It stays there forever :(

I guess I'll have to reinstall everything!

---

### Post by cyberdork33 on 2009-01-21
> **BuffaloBill said:**
> Hmm I see a slight problem.  I did the sync (almost by mistake!) and the tables are "sync" as the tool tells me.  Problem is, the Linux icon appears and then nothing.  It stays there forever :(

I guess I'll have to reinstall everything!
try reinstalling grub:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by BuffaloBill on 2009-01-22
Thanks a lot!  It's all running up again!  I got a lil penguin in extra on the rEFIt menu, but I'ld say its a less than minor inconvenient!

Thanks again!!

---

### Post by cyberdork33 on 2009-01-22
> **BuffaloBill said:**
> Thanks a lot!  It's all running up again!  I got a lil penguin in extra on the rEFIt menu, but I'ld say its a less than minor inconvenient!

Thanks again!!

Likely because you have part of GRUB in another location. You can check the information here to try and fix it:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

---

### Post by BuffaloBill on 2009-01-22
Thanks for the tip!  I'll have a look at it when I got spare time.  Honestly, having two lil pinguins doesn't bother me at all :)

For the moment, everything works like a charm and I'm really happy with Ubuntu!

Thanks for all you time!

---

