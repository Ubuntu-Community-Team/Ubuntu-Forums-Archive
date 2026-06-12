---
title: "Master Boot Record"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by viseversa on 2007-06-24
I uninstalled Ubuntu, had both Ubuntu and Vista installed. Now I can't load my Vista at all, gives me a GRUB error. How could I get my normal vista MBR back without reinstalling vista. Thanks in Advance...

---

### Post by freebird54 on 2007-06-24
Do a quick forum search on the subject.  I am sure we had this question about 8-10 days ago.  The new name for Vista to do a ***fixmbr*** escapes me at the moment :) 

The 'old' way was to run FDISK /MBR or fixmbr from a recovery console up to XP - but Vista has its own names for things...

---

### Post by freebird54 on 2007-06-24
Here's alink that may help...

[http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)

I haven't tried it - no Vista on the premises...

---

### Post by viseversa on 2007-06-24
Thanks for all the help guys but a friend told me what to do....

for anyone that needs the same help just boot with your vista cd and goto the command prompt...
then type in...

bootrec /fixboot
bootrec /fixmbr

thats all....

Thanks for the help anyways guys!

---

### Post by postalservice14 on 2007-09-16
What if you don't have a Vista CD?  I installed vista by purchasing and downloading from windows marketplace.  And installed by simply upgrading my XP Home installation.  Any ideas?

Thanks,

John

---

### Post by gj15987 on 2007-10-17
Postalservice14: Follow these instructions [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

I did it with Vista, no problems at all, just downloaded the file, typed in the command it tells you to do, rebooted and wala! Done!

---

### Post by thach562 on 2008-01-15
I basically want to do the same thing, so I booted up vista cd and deleted all the partitions and made a clean install. 

I go to start up vista and.......
I get the GRUB loader? and it's giving me an error 22. 

W..T..F. 

I thought vista overwrote the mbl when it is installed. 
At this point I'm just sick of grub. 
Is there anyway to get rid of it completely?

---

### Post by muteXe on 2008-01-15
any one if 
bootrec /fixboot
boot /fixmbr

works with xp?  Reason i ask is that i removed linux from an old dual-boot machine a few years back.  Grub is still there and boots straight into xp so so real problem, but it would be nice to get rid of grub by typing this into the dos shell in xp :)
Btw i still have linux on my main machine, so i'm not all bad :D

---

### Post by muteXe on 2008-01-15
should have been boorec /fixmbr  sorry...

---

### Post by candtalan on 2008-01-15
> **muteXe said:**
> any one (know) if 
bootrec /fixboot
bootrec /fixmbr

works with xp?  Reason i ask is that i removed linux from an old dual-boot machine a few years back.  Grub is still there and boots straight into xp so so real problem, but it would be nice to get rid of grub by typing this into the dos shell in xp :)
Btw i still have linux on my main machine, so i'm not all bad :D

I am sure you are not bad at all!  :-)

For xp I think you just use the command 
fixmbr
for example, see
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
hth

---

### Post by muteXe on 2008-01-15
ahhhh cheers for that :)

---

### Post by ByteJuggler on 2008-01-15
> **muteXe said:**
> any one if 
bootrec /fixboot
boot /fixmbr

works with xp?  Reason i ask is that i removed linux from an old dual-boot machine a few years back.  Grub is still there and boots straight into xp so so real problem, but it would be nice to get rid of grub by typing this into the dos shell in xp :)
Btw i still have linux on my main machine, so i'm not all bad :D

On XP, from the Recovery console (XP CD booted to command prompt) its the commands:

```
fixboot
fixmbr
```

---

### Post by ByteJuggler on 2008-01-17
For the record: Here's a way to restore a Windows XP MBR using only Linux tools (don't know if this works with Vista though)  [http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

---

### Post by sandysandy on 2008-01-18
with XP u can fix MBR by using Super Grub Disk.

regards

---

### Post by caravel on 2008-01-18
You can use a Win98/95 CD to fix the MBR for 2K and XP.  Just do boot from the cd and do "fdisk /mbr".  For XP/2k CDs it's "fixboot" or "fixmbr" and Vista I don't know about.

---

### Post by theinnercityhippy on 2008-02-16
Hiya Guys/gals

Hehe glad to know I'm not the only one who knacked my system in the same way. Did a bit of searching and managed to find a blog which contains a torrent and straight download for the vista recovery console .iso to boot with and use the mbrfix. I'll let you know how it goes, be interesting to find out if anyone else has success with this method?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

By the way, I'm truly hooked on Ubuntu now, despite the problems which led me to this reinstall (lesson learned, ignore anything asking you to update busybox on Gutsy!!! Be warned) so not really sure why I'm keeping windows anyway other than to remind me why I don't use it anymore.  Stay safe lovely people.

Jimdog

---

### Post by wolfwood707 on 2008-03-19
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

