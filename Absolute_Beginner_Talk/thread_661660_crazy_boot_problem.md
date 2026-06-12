---
title: "crazy boot problem"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by drascus on 2008-01-08
I awoke this morning to 

crc error 
KERNEL Panic- not syncing: VFS: Unable to mount fs on unknown block (0,0)

I checked the forum on my other computer and there didn't seem to be a solution. I think tried several things with editing the boot script. None of them worked. Then I just rebooted and for some mysterious reason everything worked again. Does anyone know what that was and what happened?

---

### Post by Shinbu-Otaku on 2008-01-08
sounds to me like a one-off boot problem, where the computer didn't recognise the boot sequence files correctly, namely one of the ones that boot the kernel, and therefore it wouldnt start. Thankfully, most of these problems get solved with a restart, as you found, but if it happens again it could be a hardware problem like your hard-drive may be on its way out...

in the mean time though, nothing major to worry about

---

### Post by philinux on 2008-01-08
You could check your hard drive with smartmontools its in synaptic.

---

### Post by drascus on 2008-01-08
thanks for the suggestion I installed it how do I run it to check to see if my drive is OK?

---

### Post by philinux on 2008-01-08
[http://www.linuxjournal.com/comment/reply/6983](http://www.linuxjournal.com/comment/reply/6983)

This should help you. Maybe your boot problem was just a one off.

---

### Post by drascus on 2008-01-08
my problem has gone from bad to worse. once again the computer won't boot giving me the same error message. Also I tried booting form a live cd and that also seems not to be working even though I know the cd is good. I am thinking that the hard drive is either really messed up or some other hardware issue. Does anyone else have experiance in this area...

---

### Post by drascus on 2008-01-09
I ran checks on the hard drive and it passed. I then ran a memtest on the ram and it failed. So I switched in some other ram and ran the test again and it passed. I have since had no problems. So this turned out to be a ram issue. 

~Thanks for all the help you guys rock~

---

