---
title: "Issues with /etc/init.d"
date: 2006-08-30
forum: Apple PPC Users
---

### Post by nits_555 on 2006-08-30
Hi,

I may have accidently deleted /etc/init.d folder. Screen dump of the normal bootup is as follows:

--------------------------------------------------------------------
INIT: cannot execute "/etc/init.d/rcS"
INIT: Entering runlevel: 2
INIT: cannot execute "/etc/init.d/rc"
(Blinking cursor)
--------------------------------------------------------------------

On trying to bootup in recovery mode:

-----------------------------------------------------------------
INIT: version 2.86 booting
INIT: cannot execute "/etc/init.d/rcS"
root@(none):~#(Blinking cursor)
root@(none):/etc# cd init.d
bash:cd:init.d: no such file or directory
-----------------------------------------------------------------

Apart from re-installation of ubuntu dapper (I have way too much programming setup on my current system, to even think of re-installing), can any of us please suggest a workaround?

Thanks,
Nitin.

---

### Post by jdong on 2006-08-30
Ouch, that hurts. /etc/init.d contains the bootup procedure for your Linux install.

The easiest way to restore it is to do a reinstall.... but if you are so motivated there might be ways to somewhat restore your system to running order. If you are interested in doing so, get an alternate install CD out in rescue mode, and we'll have some command line fun :)

---

### Post by nits_555 on 2006-08-30
Thanks for a prompt response, Jdong.

I am currently using Grub Boot Loader with an option to boot from Windows or Ubuntu. Usually, whenever ubuntu is to be re-installed I perform the following steps:

1. Use GParted to format the partition containing Ubuntu.
2. Grub Boot Loader now fails to load. I have to go ahead and run Darik's Boot and Nuke program that kills the entire hard drive (including windows partition which does not load anyway due to theGRUB screw up).
3. Usr GParted to partition the hard-drive as NTFS and ext3. Install Windows and then ubuntu.

This process is extremely time-consuming as evident, and also causes loss of critical data. Is there an easier way out of this?

Thanks,
Nitin.

---

### Post by jdong on 2006-08-30
You shouldn't need to nuke Windows... A reinstall of Ubuntu should reinstall/reconfigure grub to pick up Windows again, right?

---

### Post by nits_555 on 2006-08-30
Ok, I see what you're saying.

So reinstalling ubuntu from a backup CD would now over-write/format only the ubuntu partition and repair GRUB ? 

I have a Dapper 6.06 CD which was shipped to me by Canonical. Whenever re-install is requested, the CD runs very slowly and abruptly reports an "Installer Failed" error with an option to report the error as bug! 

Ideally it should leave the system as it was before the re-installation attempt. But on more than one occassion, this resulted into an overall screwup of the entire hard drive, resulting into the need to nuke windows.

Nitin.

---

### Post by jdong on 2006-08-30
Reinstalling Ubuntu should only touch the Ubuntu partition, and leave XP intact, and the installer's grub installer is designed to be able to detect XP and put it on the menu.

I might suggest downloading a 6.06.1 livecd, which contains some installer bugfixes. Always take the time to "check the media for defects" before installing, because there is nothing worse than having an install fail halfway through because the CD is unreadable.

If the LiveCD gives you grief, you might want to consider downloading the "alternate installer". It's less pretty but more time-tested and reliable.

---

### Post by nits_555 on 2006-08-30
Hello JDong,

I have been trying to download the Desktop CD and Alternate CD for Ubuntu 6.06.1 LTS from [http://fr.releases.ubuntu.com/6.06.1/](http://fr.releases.ubuntu.com/6.06.1/) and [http://releases.ubuntu.com/6.06.1/](http://releases.ubuntu.com/6.06.1/)

For whatever reason, the files download just fine till upto about 100 MB or so. All of a sudden, the message pops as "Download completed". While the initial download estimated is about 700 MB, the final file that is saved is about a 100 MB or so. This happened on both the URL's.

Has you ever come across a similar situation?

Thanks,
Nitin.

PS: Would be nice to know your real name. Hate calling you "JDOng" :)

---

### Post by jdong on 2006-08-30
Hmm, that's really strange. I'm not sure if you're familiar with how Bittorrent works, but I might suggest you try grabbing the torrent (from the same directory), or try using a different program to do your download...

P.s. my name is John :)

---

### Post by nits_555 on 2006-08-30
Hi John,

I have joined a group -- "Ubuntu Accessibility" and see you as one of the key members. Would be nice to have your personal email id so that independent communication can be carried out. 

Nitin.

---

