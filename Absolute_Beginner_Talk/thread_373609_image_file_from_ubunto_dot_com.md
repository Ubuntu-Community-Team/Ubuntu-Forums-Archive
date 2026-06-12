---
title: "image file from ubunto dot com"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by ascus4 on 2007-03-01
Hi all,

Ubuntu newby here.  I just downloaded the ubuntu version 6.06.1 from the ubunto site.
It's the iso file and I wrote it to CD.  Is this a bootable disk, can I install it to my HDD or does it only run from the CD?  I noticed that it has some *.exe files on the disk.  Is this normal for Linux?  I thought those were windows only file extensions.

Also, I have a dual boot laptop - WindowsXP / SUSE Linux.  Can I replace the SUSE with Ubuntu without wiping out my WinXP installation?  How do I do that and will GRUB still be the active boot manager.

SUSE is nice but I hope I'll like Ubuntu better.  It seems more popular.

Thanks in advance.

---

### Post by Maestro23 on 2007-03-01
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

It's a live CD. You can run it from the CD/DVD drive and see if you like it.  Can also go ahead and install to your HDD as well.

---

### Post by mikewhatever on 2007-03-01
To remove Suse, format the partition it is on and install Ubuntu. Grub will be installed during the last stage of the installation from Ubuntu CD and will be the boot manager. It is up to you, whether or not to wipe or to keep Windows.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by ascus4 on 2007-03-01
Same procedure as with Windows then.  Thanks.

Now I just have to figure out how to format that partition.  Windows doesn't see it.
Can I do that from within SUSE or maybe I should just use partition magic.

Thanks for the help links.  I'll check them out.

Thank you.

---

### Post by annda on 2007-03-01
you can do that during install - just choose manual partitioning and select the suse partitions to be formatted and mounted as your new ubuntu / and /swap.

---

### Post by mikewhatever on 2007-03-01
Ubuntu live cd has a nice partition manager called GParted. You can also get a GParted live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). Use the first guide I posted above, or GParted live cd documentation.

---

### Post by finferflu on 2007-03-01
As for the .exe files, they're there to try out some open source apps on Windows, such as Gaim, the GIMP, and I don't know what else...

---

### Post by ascus4 on 2007-03-01
I see that the links you posted pretty much walk you through it so I'll shut up now and read.

Thank you for your help.  

Part of the reason I'm ditching SUSE is that I cannot get most of the multimedia stuff to work.
How is it in Ubuntu?  My impression from what I read is that it's better.

---

### Post by annda on 2007-03-01
> **ascus4 said:**
> I see that the links you posted pretty much walk you through it so I'll shut up now and read.

Thank you for your help.  

Part of the reason I'm ditching SUSE is that I cannot get most of the multimedia stuff to work.
How is it in Ubuntu?  My impression from what I read is that it's better.

multimedia? no problem. just install restricted codecs from the repositories. i know, it's a step ahead, but it should give you the idea how easy it is to install most things in ubuntu and other debian based systems. the repositories are great and .deb packages do a much better job of taking care of dependencies than rpm's.

if you run out of reading material, i recommend this guide:
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

