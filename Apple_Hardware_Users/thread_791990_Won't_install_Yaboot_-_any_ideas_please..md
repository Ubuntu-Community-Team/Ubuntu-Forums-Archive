---
title: "Won't install Yaboot - any ideas please."
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by gtppc on 2008-05-12
I'm a newbie to linux. 

I have used the live cd ubuntu ppc 8.04 to try to install on my G4 powerbook - to a separate firewire drive.

It partitions and installs until the last part to do with Yaboot. The message is 'Failed to install bootloader'. This is at about 97% of the install process...

Appreciate any help.

Thank you

gtppc

---

### Post by stream303 on 2008-05-12
For now, PPC installation to an external firewire drive involves letting the install finish even though it complains about not being able to install yaboot.

You then have to boot from an install disk again, and in a shell, manually edit your /etc/yaboot.conf file.  Here is some info on how I did it - still works with Hardy, although you won't need the ofboot line:
[http://ubuntuforums.org/showthread.php?t=314237&highlight=firewire+boot](http://ubuntuforums.org/showthread.php?t=314237&highlight=firewire+boot)

This may be a bit much if you are new to Linux, so in that case, you may want to install OSX to the firewire drive, and then install Ubuntu to the internal drive.

Of course you could also dual-boot off the internal, but since you have an external firewire drive, this might be the easiest way to go for now.  In either case, backup your data! :)

---

### Post by gtppc on 2008-05-12
Grateful for that advice stream303

I will have a look at the internal drive install - and backup first!

Its late now so i will have a go at this tomorrow and let you know what happens :):)

gtppc

---

### Post by gtppc on 2008-05-14
No luck.

I backed up. Then partitioned the internal powerbook hd into 40Gb and 20Gb. then installed. Same problem when it came to the final Yaboot install.

Should I have left it unpartitioned?

gtppc

---

