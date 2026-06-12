---
title: "[SOLVED] Restoring Windows MBR - Confusing, sort of"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Drevix on 2007-09-14
I need to restore my MBR to WinXP. I’ve read a number of articles on this and quite frankly I’m confused about how to properly do this. Which do I use, my Windows cd  and the fixmbr command or my Ubuntu cd? I’m still learning Linux so I’m not familiar with the commands or procedure to do this in Linux. I’ve never had to do this particular kind of procedure before and I’m a little nervous, as I don’t want to damage or destroy any data on my NTFS partition. I kinda need to do this asap, as the drive that has my ubuntu on it is dying, and it could go at any moment.

I’m not leaving Linux altogether, just temporary until I get this problem sorted out. :-)

---

### Post by SOULRiDER on 2007-09-14
If youre gonna be dual booting you DONT want the windows booloader, you will WANT grub. Check out this link, if you have any questions just ask.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by oilchangeguy on 2007-09-14
> **SOULRiDER said:**
> If youre gonna be dual booting you DONT want the windows booloader, you will WANT grub. Check out this link, if you have any questions just ask.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

you did read the users post, right? they need to use windows, ubuntu hard drive has problems. 

using a windows xp cd, not a restore cd, or an upgrade cd, but a full version cd. boot from the cd. when prompted press R to enter the recovery console. you'll be prompted to enter your admin. password, if no admin. password, just press enter. type fixmbr and press enter. then fixboot press enter. then type exit press enter, and reboot. this should fix the problem.

---

### Post by Drevix on 2007-09-14
I'm not going to be booting anything unless I restore my MBR to windows. The slave drive I installed Ubuntu on is dying and without that I can't boot into windows, which is on my master drive.

---

### Post by oilchangeguy on 2007-09-14
> **Drevix said:**
> I'm not going to be booting anything unless I restore my MBR to windows. The slave drive I installed Ubuntu on is dying and without that I can't boot into windows, which is on my master drive.

see post #3.

---

### Post by splintercellguy on 2007-09-14
I use Super GRUB for my MBR needs.

---

### Post by Drevix on 2007-09-14
Sorry oilchangeguy, I was replying to soulrider.

I assume that my WinXP cd is full version since it will do a full install on a new system with no OS on it.

I guess the only way to find out is to put it in, boot up to cd, and see what happens. :-)

---

### Post by raycosm on 2007-09-14
> **splintercellguy said:**
> I use Super GRUB for my MBR needs.

I didn't have an XP cd, only a recovery disk (damn you laptop manufacturers!), and I  used Super GRUB Disk to restore the MBR, and that seemed to work. Even though it's a "GRUB disk" it will fix your XP MBR.

---

