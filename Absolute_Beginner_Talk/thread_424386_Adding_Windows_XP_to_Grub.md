---
title: "Adding Windows XP to Grub"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by ryanchead on 2007-04-26
OK, so I am dual-booting Ubuntu 7.04 with Windows XP Professional across 3 hard drives.

Ubuntu is on a SATA hard drive.

Windows XP is on two IDE hard drives. Windows was installed first on the two IDE drives, and then I added an SATA drive when I installed ubuntu, so Windows should have its own MBR on the primary IDE drive.

Right now, in order to switch between them I have to change to boot priority in the BIOS. I have tried editing the menu.lst, but can't get it to work. Sometimes I get error codes, and sometimes I get nothing. The following entry gives the message "Starting..." and then does nothing.

title  Windows XP Pro
root  (hd1,0)
makeactive
chainloader +1

Any ideas?

---

### Post by laidback on 2007-04-26
Check here:-
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)
as there have been some changes to grub for Feisty Fawn.

And here for grub manual:-

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

I believe also you should check carefully the IDE vs Sata issue. Seem to remember reading something about it but as I don't have Sata yet I didn't take a lot of notice. If I see it again I'll post it for you.

Cheked through my notes and I cannot find the Sata ref, maybe a mistake on my part, but, in grub page (as above) there is a ref to using USB drives as these are treated as SCSI drives, which alters the numbering of the hdd's (hd0, hd1 etc)

Grub Page is really worth a read.

---

### Post by Duck2006 on 2007-04-26
title Windows XP Pro
root (hd1,0)
makeactive
chainloader +1

add map lines so it looks like this

title Windows XP Pro
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by ryanchead on 2007-05-11
I just got a chance to work on the system again. Thanks for your help. Adding those two map lines fixed the problem.

Thanks again.

---

