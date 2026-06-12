---
title: "CD UBUNTU 7.04 32 bit for PC will not boot"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Manyette on 2007-05-23
Baffled.  Just received 7.04 CD's, have tried two of them, and PC fails to boot.  Pentium 4 (socket 478) 2.8 Ghz
on a working PC running Windows XP pro.  2 gigs of memory.  Trying to run the "live" version of Ubuntu.  Cd reads in fine, displays Ubuntu logo, then says cannot start tty.  Then gives three error messages znd dies completely.  There is nothing on the pc which is "cutting edge" and is at least a generation out of date.  Have read all the help files here, but they all assume that at the very least the CD has booted.

---

### Post by Cypher on 2007-05-23
What error messages?

---

### Post by lazyart on 2007-05-23
Check CD for defects (main menu of Live CD)?

---

### Post by Manyette on 2007-05-23
> **Cypher said:**
> What error messages?

Sorry for delay, had to reboot for details.  Errors as follows:
Can't access tty:  job control off
35.115495  ata2 01 xfer mode off err masmk 0x04)
70.881840  ata2.01 xfer mode off err mask (0x04)
111.651563 ata2.00 xfer mode off err mask (0x40)

At this point, nothing further happens for over 10 minutes

Hope these mean more to you than they do to me!  LOL  And thanks.

---

### Post by Manyette on 2007-05-23
> **Cypher said:**
> What error messages?

Doesn't work!  When trying to check the CD, same set of error messages, and
then it dies.

---

### Post by aks44 on 2007-05-23
I had the very same problem. It relates to a bug in newer 2.6.??? kernels that have problems with some older ATA CD/DVD readers and/or writers. The bug is described here : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410)

Try booting on another CD/DVD drive, and/or disconnecting all but one. Be aware that if you ever manage to install Ubuntu, you'll have to add the "irqpoll" kernel option as described in the bug report in order to have your CD/DVD drives be recognized.
Your boot time will also be very slow (maybe several minutes) until you set that kernel option.

I guess on the LiveCD you can tell the kernel to use "irqpoll" but I don't know how... maybe someone more knowledgeable here can tell how.

Fortunately, a kernel fix has been posted so it is only a matter of time for this bug to be fixed in the "mainstream" distribution.

Good luck anyway, as far as I'm concerned I found it was well worth the effort !

**Edit:**
In fact, the instructions for adding the kernel "irqpoll" option to your freshly installed GRUB are there : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826)
Still no clue how to specify it for booting the LiveCD though...

---

### Post by Manyette on 2007-05-23
Thank you very much.  Moved CD from Mitsumi Combo drive to old TDK CD drive, and it booted just fine.  I am now running this post from Ubuntu Live.  Posting this in the hope it might help some other newbie.  I'm a retired software engineer who hasn't dealt with *nix in 25 years.  Have lived in the PC world for all that time.  So far I am much impressed with how far *nix systems have come.  Again, thank you.  Time to install another drive to hold Ubuntu.

---

### Post by Sudhanshu on 2007-05-30
Press F6 when "Start or Install" is selected on the LiveCD menu options to access the boot options. Use the irqpoll before the -- at the end of line.

---

### Post by Manyette on 2007-05-30
Thanks for the tip.  I did get it to work in another drive, but it's nice to know I can use either drive with this tip.  Again, thank you.

---

