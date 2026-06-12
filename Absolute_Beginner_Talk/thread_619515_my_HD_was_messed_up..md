---
title: "my HD was messed up."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by danezeq on 2007-11-21
Help me!!!
i installed vista.
then i installed ubuntu.
then i installed XP.
my HD was messed up.

On booting the computer stuck. no error message.
i can boot only with floopy or boot cd. (and with other hard disks)
when i run FDISK from a rescue disk i can see a partition which i CAN'T delete! (i suspect this is the problem)


i want to start from the begining. as if the HD was brand new from the store.

Is there any way making the hd factory-set? (stronger then Format and Fdisk)

---

### Post by bluepowder7 on 2007-11-21
do you have original install CD's for Vista and XP?

what you SHOULD do is (in order):

install XP
install Vista
install Ubuntu

microsoft themselves say that their OSes should be installed oldest first, so you'd do 95, then 98, then 2k, then xp, and then vista.  or just pick the ones you want, but stick to that order.

on my desktop, i installed 2k, then added xp, and then added ubuntu.  it all works fine, and i didn't need to do any special manual setup of the various boot options.  the ONLY difficulty was that i had to install xp from within 2k (meaning, i couldn't boot into the xp install disk - i had to run the setup.exe file that's on the winxp cd while i was using win2k).

---

### Post by danezeq on 2007-11-21
No no! you don't understand!
Something VERY wrong happend to the hd.
the XP setup stuck right after the first reboot! (Vista setup stuck even before the reboot - it gives a blue screen with long error message)
when i run fdisk i can see a partition - and i can't delete it. it's not possible.

i need to get rid of that partition (it catch almost 50% disk space) is it possible doing that via Fdisk?

---

### Post by bobpur on 2007-11-21
Try going to [www.distrowatch.com](www.distrowatch.com) and downloading gparted or pmagic and using them to try to partition. I have better luck with them than about anything else. Also you might try System rescue cd.
As long as your problem isn't mechanical they should do the job.

                                             Good Luck.

---

### Post by bumanie on 2007-11-22
Do I understand you properly? These are completely new installs and you don't have saved information on the drives. You want to return your hard drives to 'pristine' condition. If this is correct the best thing to do would be to download dban and wipe your drives with that and start fresh. If I am barking up the wrong tree let me know and I will try and work something else out if I can.

---

### Post by danezeq on 2007-11-23
surprisingly the solution was to get rid of that partition via win xp installion!!
fdisk can't delete it - and xp installion CAN?!

wierd!

but thank you all :)

---

