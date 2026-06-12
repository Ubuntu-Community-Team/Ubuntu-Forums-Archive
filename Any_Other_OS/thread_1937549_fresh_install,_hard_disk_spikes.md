---
title: "fresh install, hard disk spikes"
date: 2012-03-08
forum: Any Other OS
---

### Post by deskman on 2012-03-08
i just installed wheezy with gnome 3 on 100G
partition. it is a fresh install so i didnt add any
programs except of synaptic and nvidia driver. i
noticed increased disk activity: for example
1) when i moove the cursor to the "activities" at
the top left, the hard disk makes a short (1 sec)
sound and the led blinks
2) when leave the pc untouched, the hard disk
led blinks every 5 seconds and there is a short
grinding noise every time.
it doesnt happen in windows7 or mint install on
the same machine.
can it be kind of "bad" installation or errors
during partitioning or installation process? or it
can be related to the software or something
else?

---

### Post by sikander3786 on 2012-03-08
Most probably, it is a hard drive failure. By chance, Debian Wheezy installed itself to the portion of HDD which isn't as healthy as the rest of the HDD where Windows 7 or Linux Mint are installed. You better download HDD diagnostic tools from the manufacturers website and test your HDD. If it is failing, backup your data and transfer it to a new HDD as soon as possible.

---

### Post by Elfy on 2012-03-08
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by deskman on 2012-03-08
the hdd test is ok. by the way sorry i didnt mention it before, but mint was installed in the same space that wheezy is installed now. i mean i deleted mint and installed wheezy. the only change is that mint was had 8G swap and debian automatic partitioner changed it to 4.

---

### Post by sikander3786 on 2012-03-08
A normal HDD scan might run over-night. You mean you've already tested your HDD?

Other than that, I've got no pointers regarding your problem. Some-one else might have some suggestions though.

---

### Post by deskman on 2012-03-11
i performed a scan with application from WD. it is not overnight but the results were competely ok. i reinstalled the OS and now everything seems to be perfecto.
the only question i have now is : when u install a bunch of codecs and drivers in linux and then reboot into windows, can it cause some performance issues later on alinux partition?

---

### Post by deskman on 2012-03-11
when u install a bunch of codecs and drivers in linux and then reboot into windows, can it cause some performance issues later on alinux partition?

---

### Post by 2F4U on 2012-03-11
Installing drivers can cause performance issues, but I don't know of any codec that would cause that unless it is used. I also haven't seen a performance degradation on Linux just from rebooting into Windows.

---

### Post by darkod on 2012-03-11
In proper dual boot the OSs are separate and "invisible" to each other. Installing something on one can't have influence on the other.

Of course, as already said, installing some driver or software can cause issues sometimes (depends), but the issues will not be because you are dual booting with windows. If any software creates issues it would do it also when ubuntu is the only OS.

---

