---
title: "/home partition"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by IamAcoconut on 2007-02-25
Is it necessary to have home on a separated partition? I mean, is it bad to keep all the data on one partition? I ask, because I'm using LUKS and it's tricky to set up other partitions then root to  be decrypted and mounted @ boot time, and since I only use Linux...

---

### Post by taurus on 2007-02-25
It is a good idea to have a separate /home so that when you reinstall, you can keep all your personal settings.  Otherwise, formatting before installing will wipe out your personal stuff which means you need to do a backup first before you reinstall.

---

### Post by r4ik on 2007-02-25
If you installed already and want to create one this might help,

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck !

---

### Post by tageiru on 2007-02-25
You could create a separate home partition and use LUKS with a key file which you store on the root partition. That way you only need to supply the password for the root partition when you start the computer.

---

### Post by IamAcoconut on 2007-02-25
So it's no harm for the system, to keep all the data on the same partition, right?

---

### Post by tageiru on 2007-02-25
> **IamAcoconut said:**
> So it's no harm for the system, to keep all the data on the same partition, right?

No

---

### Post by x1a4 on 2007-02-25
Hi,

If you're planning (or at least see it as a possibility) to install another distro some time in the future, the downside of having your /home directory on another partition is that your settings may not be 100% compatible with the new distro and cause problems.  

On my computer I have a separate partition for all my documents (music, videos, office docs etc.) which is mounted on /docs and symlinked in my home directory.  I also periodically backup my global & user settings in /docs.  This way, whenever I installed a new distro I had all my documents untouched and could copy only the settings files appropriate to the new distro.

---

### Post by IamAcoconut on 2007-02-25
All the info I needed, thanks!

---

### Post by houstonbofh on 2007-02-25
You might not have realized it, but you stumbled into a theological discussion here. :)  My personal choice is to have only one partition unless there is a real reason not to.  Here are some partitions I have used, and why.

/boot - I had a hard drive too big for the BIOS to read.  If the files in /boot are not in the front of the drive, guess what happens here?  This is only needed if the HD controller can't see the entire drive from the BIOS, or for some older RAID controllers.  (Compaq, and DAC960)

/var/log - A server.  A hacker trying to kill us filled up / and the system was DOA.  It took a while to figure out why...  On rebuild, this was the fix.  It was an Internet facing application server.

/home - Already covered.  The only time I did it was when I had a stable and a testing version on one box.  I thought I was clever until the testing version crashed my mail profile. Doh!

/various - Name for a extra RAID array, or SAN, or network mounted disk.  Sometimes used by a cluster...

---

### Post by benuski on 2007-02-27
If I test out other distros on the same hard drive, will the ignore my /home partition, or will they try and use it as their own /home partition?

---

