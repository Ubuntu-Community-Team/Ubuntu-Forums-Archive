---
title: "Ubuntu 7.10 doesn't boot, BusyBox shell..."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by DouweI on 2007-12-02
Hey guys,

A week ago, I installed Ubuntu 7.10 Gutsy using Wubi. Everything went fine, I love Ubuntu, but today something strange happens:
When I start up my laptop I can choose Vista or Ubuntu, off course I choose Ubuntu. The loading-bar appears, does nothing for a few seconds, and then; the Busy Box 1.1.3 shell-thing pops up, so I don't can get into Ubuntu... :(

I just tried running Ubuntu in recovery mode, by pressing ESC just before the loading-bar. A lot of text comes by, and on the bottom I see the following:
mount: Mounting /root on /host failed: Invalid Argument
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!
Followed by the same BusyBox as I see when starting normally...

Does anyone know what I can do to fix this? I am kinda Linux-n00b...

Thanks in advance, Douwe

PS. I see the word 'disks', and somewhere else on the internet I read something about BusyBox and new harddrives, but the only hardware-thing I did in the last week/yesterday was connecting my HP printer...

---

### Post by DouweI on 2007-12-11
Someone :(

---

### Post by stmiller on 2007-12-11
Might be related to a powerpc bug where Gutsy does not load the ide module needed. Check out this page for a possible fix:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by DouweI on 2007-12-15
Thanks, but for as far as I know is PowerPC Mac... I am using a Acer laptop which comes with Windows Vista (:-&)

---

### Post by rockpenguin on 2007-12-19
Hey douwel,

Dunno if you fixed the issue yet... I had the same problem and I stumbled across this post:

[http://ubuntuforums.org/showthread.php?t=295508]("http://ubuntuforums.org/showthread.php?t=295508")

I did the "aptitude reinstall ubuntu-minimal" part and that seems to have done the trick.  I'll keep my fingers crossed.  Hope that helps!

---

