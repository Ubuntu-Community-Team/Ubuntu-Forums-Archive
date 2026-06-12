---
title: "Mount problem using sshfs - I/O error copying large files"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by thethendi on 2008-03-15
Hi all,

I am trying to network two computers, both running Ubuntu 7.10, using sshfs to Mount the drives from my Desktop computer to my laptop.  For this, I use sshfs with the following syntax:
```

sshfs username@192.168.xxx.xxx:/media/hda5 ~/Mounts/Media
```

I have the openssh server (I installed the packaged openssh-server) on the Desktop computer.

I can copy small files back and forth no problem, but when I try to copy larger files from my laptop to the mount point, I get an "I/O error" and the mount disappears.  I tried restarting router, same thing happens.

Any ideas?

EDIT: Copying files from the desktop to the laptop works fine, but I get the error when I try to copy from the laptop to the desktop.

---

### Post by dcstar on 2008-03-15
> **thethendi said:**
> Hi all,

I am trying to network two computers, both running Ubuntu 7.10, using sshfs to Mount the drives from my Desktop computer to my laptop.  For this, I use sshfs with the following syntax:
.......
EDIT: Copying files from the desktop to the laptop works fine, but I get the error when I try to copy from the laptop to the desktop.

Check flow control on the network connections, there may be an issue on one of the machines.

---

### Post by thethendi on 2008-03-15
Sorry, how would I do that?  (I'm still learning how to use Ubuntu and Linux in general).

When I check using "Network Tools" (System>Administration>Network Tools), I can ping the Desktop machine with 100% packet transmission, and I see that the SSH port is open on the machine.  I don't know if that helps any.

Thanks.

---

### Post by thethendi on 2008-03-15
Update:

It seems that the problem only occurs when I boot into the "realtime" kernel on my desktop.  When I boot into the 2.6.22.14-generic kernel, sshfs works fine.

So I don't know if the problem is necessarily solved; but why would it work for the generic kernel and not the rt kernel?

---

