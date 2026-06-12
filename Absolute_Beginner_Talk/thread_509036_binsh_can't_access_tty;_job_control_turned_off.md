---
title: "/bin/sh: can't access tty; job control turned off"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by intransit on 2007-07-24
Hi all,

just did the following steps

1) insert ubuntu live boot cd (and i definetly know that this works as it was working yesterday)

2) reboot laptop

3) select start ubuntu in safe graphics mode

4) get error

```

BusyBox v1.1.3 (Debian 1:1.1..3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

```

What's going on? The CD was running live mode fine just yesterday. I don't get it

---

### Post by dhopley on 2007-07-25
Dear Intransit , 
Hi , I've a legacy dual boot 98SE and Fiesty Faun set up and have suffered intermittent tty job control initramfs errors at start up , if you enter alt-ctrl-F1 or alt-ctrl-F2 or alt-ctrl-delete you will elicit further responses to the boot up . The problem seems to be related to a weakness in the automatic recognition of the hardware set up and the bin/sh is simply a statement of failure . Frequently the action of restarting via alt-ctrl-delete works , but I've also restarted from the recovery modules in the Grub reboot . In my case the problem is more likely after non standard shutdowns , so my suggestion is that you review your previous session and consider if anything may have changed your hardware configuration to upset Ubuntu . Apparently this weakness is scheduled for improvement in Gutsy Gibbon (due October) . Good luck ,    
Derek

---

