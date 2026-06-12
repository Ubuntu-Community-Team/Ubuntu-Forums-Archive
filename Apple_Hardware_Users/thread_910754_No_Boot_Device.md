---
title: "No Boot Device"
date: 2008-09-04
forum: Apple Hardware Users
---

### Post by niteblind on 2008-09-04
Hi All.

I went to reinstall my ubuntu gutsy and there appear to no longer be any repositories any more. Oh well never mind I thought I will finally get around to upgrading to Hardy Heron.

Every time I install Hardy everything goes fine but when the PC restarts at the end it does not boot back up again to Ubuntu. The Mac OS is seen but if I try to specify the ubuntu partition I get the error:

No Bott Device... Please insert a bootable cd.

Does anyone know what is going on? Anything I can do?

Please help
niteblind

---

### Post by knattlhuber on 2008-09-04
OK, just for clarification: You're on a Mac with a dual boot OSX/Ubuntu. Correct? I assume you are using 'refit' as the boot manager?!

---

### Post by knattlhuber on 2008-09-04
Found the thread that fixed the problem for me: [http://ubuntuforums.org/showpost.php?p=3303463]("http://ubuntuforums.org/showpost.php?p=3303463")

There may also be some useful info in this thread: [http://ubuntuforums.org/showthread.php?t=767677]("http://ubuntuforums.org/showthread.php?t=767677")

---

### Post by cyberdork33 on 2008-09-04
> **knattlhuber said:**
> Found the thread that fixed the problem for me: [http://ubuntuforums.org/showpost.php?p=3303463](http://ubuntuforums.org/showpost.php?p=3303463)

There may also be some useful info in this thread: [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)
Yes, the immediate answer is in the second link. You should not have to reinstall grub unless absolutely necessary.

---

### Post by niteblind on 2008-09-05
Hi.

Thanks for the responses I will try this now. while I am though can I pose another question on a similar topic.

Ecer time I try and triple boot my mac with WinXP it never seems to work. As soon asI install linux after installing win XP I get the following error when I try to boot windows:

The following file is missing or corrupt
c"|windows|stste|hal.dll.

would this be caused by the same issue as that file is perfectly fine right up until the point I install the 3rd OS.

Cheers

---

### Post by cyberdork33 on 2008-09-05
> **niteblind said:**
> Hi.

Thanks for the responses I will try this now. while I am though can I pose another question on a similar topic.

Ecer time I try and triple boot my mac with WinXP it never seems to work. As soon asI install linux after installing win XP I get the following error when I try to boot windows:

The following file is missing or corrupt
c"|windows|stste|hal.dll.

would this be caused by the same issue as that file is perfectly fine right up until the point I install the 3rd OS.

Cheers

If you create all the partitions you need before installing anything, then you won't have that problem. Windows doesn't like it when you play with the partition table after it has already been installed.

---

### Post by niteblind on 2008-09-05
Through the numerous times I have resintalled and partitioned and attempted to get the piece of junk that is XP to install and then stay stable I can catagorically say that on my Macbook at least that does not work.

As doon as I install the 3rd OS  be it Gutsy Hardy or Redhat  the Windows partition goes tits up and to be honest I am fed up trying to get the thing working so I dumped the XP partition and I will now just dual boot it.

The only reason I was desperate to get it on there was that I wanted to run the Testout Linux+ software and they only make it for windows. Now how screwed up is that!

Thanks for all the advice btw after using the partition tool in refit my Hardy install is now up and running.

Cheers
niteblind

---

