---
title: "D/loading Ubuntu now, couple of questions."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by DaveElson on 2007-06-10
Hello All
I have an older AMD Athlon computer that is home built, and that I cannot (for some reason) upgrade to Windows SP2 (it crashes it, even with the "fix").
So I've decided to try Linux. I had heard of Ubuntu some time ago and it has been suggested by a couple of users.
Anyway, I'm downloading right now and my first question is (I didn't see it mentioned in the online docs) can I have dual bootup options with Windows, at least until I'm up and running okay with Ubuntu?

Q - 2. I have a wireless Linksys 2.4 ghz usb adapter on the machine, with the cable modem on my wife's business comp. Am I likeley to have many headaches setting this up?

I played around with Linux many years ago  just to have a look. I'm happy to migrate, in fact I'm looking forward to it (may help stop this machine freezing and crashing so often) and appreciate any advice. This machine is used really just for my online email and a little bit of torrenting, I have another that's more "modern" so I have no problems should it not quite work out okay, but I'm sure most things can be fixed. I will want to burn cd's and dvd's with this if possible.

All the best.

---

### Post by jba6511 on 2007-06-10
yes you can have a dual boot situation with ubuntu and xp. There are plenty of guides available for doing this. as far as the wirless situiation, and can not really comment on that but others will be able to help out. Ubuntu comes with a built in utility to burn cds/dvds as well. It will be under places. Good luck

---

### Post by durrell on 2007-06-10
You should have no problem at all dual booting alongside Windows. As long as you don't tell the Ubuntu installer to install on the entire hard drive, and you leave your Windows partition intact, the Ubuntu installer will configure it to dual boot Ubuntu and Windows by default. Make sure whatever version of Windows you're going to install gets installed before Ubuntu, because if you install it afterwords Windows will overwrite your GRUB boot loader (the dual boot loader) and you'll only have access to Windows.

As for the other question, I'm not sure..maybe someone else will have some input on that.

Here is a great dual boot guide if you want to do the partitioning yourself like I did:
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

---

