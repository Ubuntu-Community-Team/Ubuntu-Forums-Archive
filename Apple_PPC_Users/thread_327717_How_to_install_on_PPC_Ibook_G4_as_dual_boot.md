---
title: "How to install on PPC Ibook G4 as dual boot"
date: 2006-12-29
forum: Apple PPC Users
---

### Post by Lend27 on 2006-12-29
I am not new to Linux, but new to Ubuntu.
I have used Debian distros as dual boot on a windows PC.
Now I'd like to install Ubuntu as a dual boot on my Ibook G4.
Is there a guide available for this process?

Thanks for the info!

Len

---

### Post by linear on 2006-12-30
You can find general instructions [here]("http://www.ubuntuforums.org/showpost.php?p=755739&postcount=4").

---

### Post by handylinux on 2006-12-31
I'm new to Linux & Ubuntu, after 18 years on the Mac OS; so I'm far from expert, but have figured out a few things installing Ubuntu on my iBook G4 along with OS X, including that for ease in dual-booting, you should **install Linux on the first partition**.

For details of my experiences, and recommendations, see:
**[How to switch OS on dual-boot Mac]("http://www.ubuntuforums.org/showthread.php?t=318682")**
**[OSX and ubuntu dual boot on an 80GB HD mac mini 1.42]("http://www.ubuntuforums.org/showthread.php?p=1951103")**

---

### Post by dpny on 2007-01-02
My two cents:

I installed Ubuntu on my old PIsmo. The process was pretty straightforward. I:

1) Formatted the drive;
2) Created two partitions of equal size (~ 20 gigs each) using Apple's disk utilty;
3) Installed the Apple operating systems, in my case 9.2.2 and 10.4.8. Apple's installers don't work for dual booting at all. In other words, if you install Ubuntu first Apple's installers won't play nice;
4) Started up the Ubuntu PPC CD by rebooting and holding down the "C" key;
5) Let the installer do its thing. The only difficulty I had was forgetting to tell the installer to format the partition I had left blank for Ubuntu as ext3. I  kept getting stuck on this step until I figured that out;
6) There is no step 6.

For the record, I do not have Ubuntu installed on the first partition and have had no problems.

---

### Post by handylinux on 2007-01-02
> **dpny said:**
> For the record, I do not have Ubuntu installed on the first partition and have had no problems.
How do you switch from Mac OS to Ubuntu? My guess is that you press the option key during startup, wait for the selection screen to finish loading (which takes a while), click on the Linux partition, then click the "continue" arrow? Of course this is not a "problem", but it is rather tedious; anyway I found it so. My suggestion to put Ubuntu on the first partition is not to avoid "problems", but to simplify the switch, so all you have to do is press the D key during startup: one quick step rather than four slow steps.

---

### Post by dpny on 2007-01-02
> **handylinux said:**
> How do you switch from Mac OS to Ubuntu? My guess is that you press the option key during startup, wait for the selection screen to finish loading (which takes a while), click on the Linux partition, then click the "continue" arrow? Of course this is not a "problem", but it is rather tedious; anyway I found it so. My suggestion to put Ubuntu on the first partition is not to avoid "problems", but to simplify the switch, so all you have to do is press the D key during startup: one quick step rather than four slow steps.

No. When the machine starts up I get the yaboot menu which gives me three choices: "X" for OS X, "L" for Linux and "C" for CD. As the machine is booted into Ubuntu 99% of the time and rarely rebooted, I don't see the menu all that often.

---

