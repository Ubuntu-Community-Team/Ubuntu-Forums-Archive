---
title: "Fresh Install and Very Slow Performance"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by pancakelizard on 2007-06-27
After a weekend of testing Ubuntu 7.04 from a LiveCD, I decided to create two partitions and dual boot Ubuntu (ext3) and Windows XP Professional (ntfs).

I figured on a dual 3.0 gHz with 3.5gigs of RAM and a 10k RPM HDD, performance wouldn't be an issue. Well I guess I was wrong.

Unlike the LiveCD, the installed copy runs slower than anything I've seen. Maybe someone can shed some light on this.

Loading 2.6.20-16-generic

At the inital loading screen, it takes about 3 minutes for the status bar to move and there isn't any HDD noise so I'm assuming no activity.

After, I get the error 181.447563 iTco_wdt: failed to reset NO_REBOOT flag, reboot disable by hardware. 
It doesn't freeze here, just shows the error message.

The next freeze spot is at:
Starting hardware abstraction layer hald 
Another minute or so it freezes

Once the login screen comes in, the display takes forever to show up (i have a nvidia geforce 4 with the drivers installed) however I can't get a resolution higher than 1024x768.

Some other annoyances:
The Ubuntu help center is constantly opening new instances of itself. It did this during the live cd and while annoying, I assumed this was because it was a livecd. Right now I have over 70 instances of it open. If I close the group, more open.

Also in System - Admin (menu) Keyring Manager is the first item. Is it normal to start in the 'k's?

And btw yes, I did a system update on files (which also took forever) assuming that could fix the issue.

---

### Post by Nussbaum on 2007-06-27
I'm no linux expert but if running it from the cd is faster then from your harddrive then something is wrong. Since you seem to have partitioned your own hd, did you create a swap partition?

---

### Post by pancakelizard on 2007-06-27
I let the install package deal with the partition setup through guided mode. I remember seeing a swap partition listed in the final steps, how do I verify this?

---

### Post by Nussbaum on 2007-06-27
if you type gedit /etc/fstab  it should have a list of your partitions and it should be there. For your resource use you could look at system > administration > system monitor which shows your ram and swap usage. I dont know if thats your problem though so might be something else entirely. (seeing as booting it from the CD it probably doesnt use swap either and pcs having so much ram these days might not be a problem anymore)

---

### Post by night_raiders on 2007-06-27
one of these threads should have your problem for your screen resolution
[http://ubuntuforums.org/showthread.php?t=484547](http://ubuntuforums.org/showthread.php?t=484547)
or
[http://ubuntuforums.org/showthread.php?t=484622](http://ubuntuforums.org/showthread.php?t=484622)

---

### Post by pancakelizard on 2007-06-27
> **Nussbaum said:**
> if you type gedit /etc/fstab  it should have a list of your partitions and it should be there. For your resource use you could look at system > administration > system monitor which shows your ram and swap usage. I dont know if thats your problem though so might be something else entirely. (seeing as booting it from the CD it probably doesnt use swap either and pcs having so much ram these days might not be a problem anymore)

Here is the output of the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e2e891a4-46dc-4c0c-82e1-0cc3e958489e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7c6c215b-d34b-485a-a60a-6f47620ea820 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I have a swap partition showing however the ext3 partition is showing an error.

Also, how do I get the Ubuntu Help Center to stop coming up? It seems that whenever I type on the keyboard more instances of it continue to popup as well.

---

### Post by pancakelizard on 2007-06-28
> **night_raiders said:**
> one of these threads should have your problem for your screen resolution
[http://ubuntuforums.org/showthread.php?t=484547](http://ubuntuforums.org/showthread.php?t=484547)
or
[http://ubuntuforums.org/showthread.php?t=484622](http://ubuntuforums.org/showthread.php?t=484622)

Thanks, this fixed it! 
Well the resolution anyway

---

