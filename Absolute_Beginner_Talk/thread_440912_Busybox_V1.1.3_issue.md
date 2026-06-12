---
title: "Busybox V1.1.3 issue"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by tadcan on 2007-05-12
Hi 

When I boot with the CD I get this message.

Busybox v1.1.3 (Debian 1:1.1.3-3unbuntu) Built in shell (ash)
Enter 'help' for a list of built-in commands

/binlsh: can't access tty; job control turned off
(initramfs) 

I had a look and found the same problem elsewhere I tried this fix

Boot computer, press F6 at menu, type *break=top* into the line that appears. Then typed *modprobe piix* pressed enter and then typed *exit* and enter

I just ended up in the same place again with the above message.

My machine is a Athlon x2400+ 2.01Ghz 1GB ram, 80 GB HD

I know othewr solutions were posted, but they went over my head.

---

### Post by tadcan on 2007-05-13
*bump*

---

### Post by demonzrulaz on 2007-11-04
bump

---

### Post by chris.m.ball on 2007-11-04
I actually saw similar issues a while back when booting from the CD.  I managed to get around this issue by re-burning my ISO image at a slower write speed.  I also had to completely power on and off my system before the new CD would actually boot correctly.  Hope this helps.

---

### Post by milpillas on 2007-11-06
I _had_ the same problem.
In my case I had 2 optical drives: a CD burner and a regular 56X cd drive. My first optical boot was the CD-RW.  After several weeks of frustration, I disconnected the CD writer and only used the regular 56X CD-R drive. To my surprise  NO more error.  It booted up fine and I'm installing it right now.
Not sure if the source of the problem is the fact that the configuration does not like 2 cd drives or my original CD-RW drive has a problem.

---

### Post by korblackdog on 2008-06-08
hi that error because of the optical drive change your optical drive and your problem will be solved. thnx all by by.

---

### Post by dubliner_tallaght on 2008-07-05
Hi. I had the same pb on my computer. I have 2 OS (Kubuntu and XP) on the same Drive. And on Xp I installed Magic Iso to have Virtual CDROM reader. After uninstalling Magic Iso, no pb anymore.:). Hopefully it could help !

---

