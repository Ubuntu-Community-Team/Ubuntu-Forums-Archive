---
title: "job control turned off   (help please)"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by mock47 on 2006-09-15
I believe that I broke something.  After installing Gnomeppp my machine would not access my modem.  It went to command line and I do not know what to do. The following is the read from the attempted boot I hope someone can help.

Uncompressing Linux. . .  ok, booting the kernel.
mount: Mounting /dev/hda1 on /root failed: invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enmter 'help' for a list of built in commants.

/bin/sh: can't access tty; job control turned off



hopefully, this means something to someone.

I have command line access only.

Art

---

### Post by lefty_lou on 2006-10-06
I have the same exact problem  but can't seem to find a way of fixing it. I read around but can't understand half the stuff as a noobie already had the problem before and reinstalled breezy decided to try the update again today and still the same problem...how do you expect people like me to change to UBUNTU (linux) if it's all so hard and difficult plus when we read around is all explained in linux terms and not for the rest of us trying it. Help !!!!!! pleaseeeeeeeeeeeeee..](*,) :evil: :(

---

### Post by lefty_lou on 2006-10-11
well i guess i'm stuck with windows...oh and by the way thanks for the help made my UBUNTU experience totally a disaster.

---

### Post by whimbrel46 on 2006-10-11
- I have alsmost exactly the same problem. Difference is that on my computer the error message is "..../dev/sda1..." as I use SATA disks.
- This is something triggered by a change in disk configuration.
I tried to create a dual boot option via the BIOS. I installed Ubuntu 6.06 on a separate harddisk, with my windows disk disconnected. I then reconnected my Windows disk. Booted  from Ubuntu disk (via BIOS): OK. Booted Windows disk (via BIOS): OK.
Tried to boot Ubuntu disk: fail (above message). So, somehow, either Ubuntu is very sensitive to changes or Windows XP makes modifications to the Ubuntu disk.

---

