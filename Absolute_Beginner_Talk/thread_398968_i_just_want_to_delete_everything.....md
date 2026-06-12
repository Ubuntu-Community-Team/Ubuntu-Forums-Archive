---
title: "i just want to delete everything...."
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by CorranSW on 2007-04-01
i have had ubuntu installed on my desktop before in partition with windows and fedora core 6.... i erased it along with every partition i have had.... tryed to reinstall it froze up the only OS i could install was fedora.... i dont feel like explaining everything because i have posted on the forum a dozen times without receiving any help.... i just want windows back.... o.k. without being able to access anything but fedora core 6 and my bios... how do i completely erase my hard drive? Just dont ask any questions on the thread because that has never gotten me anywhere on the site... just give me the command to completely erase the drive please....

---

### Post by chalex on 2007-04-01
To completely erase your hard drive, it is easiest to use a bootable floppy/CD like DBAN or the hard drive manufacturer's utility disk.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

You could also boot from the Ubuntu LiveCD and use the Parted program.  Of course, they also have their own LiveCD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by STREETURCHINE on 2007-04-01
use gparted to format your hard drive ,and reinstall what ever you want,

---

### Post by mac.ryan on 2007-04-01
Boot you system with ubuntu liveCD, then use gparted to remove all your partitions. Then reboot from the window$ installation CD and... voilà :o

Anyhow, if you simply want to reactivate you presently installed version of windows, what you have to do is fixing the MBR (assuming windows was the first system you installed on your computer...).

---

### Post by CorranSW on 2007-04-02
As i said i cant use the live CD it doeent boot

---

### Post by pataphysician on 2007-04-02
just boot to your windows cd and format the drive during the installation

---

### Post by CorranSW on 2007-04-02
as i said i cant boot to anything... exept fedora core 6, i am typing on my dell xp m1710 right now...

---

### Post by oilchangeguy on 2007-04-02
is the computer set to boot from the cd drive first?

---

### Post by pataphysician on 2007-04-02
> **CorranSW said:**
> as i said i cant boot to anything... exept fedora core 6, i am typing on my dell xp m1710 right now...

if you can't boot to the windows disc now, you won't be able to when you need to install windows, either. formatting from within fedora, or doing anything from within fedora, won't get windows back on there. you need to go into your bios and set the cd drive as the first boot device.

---

### Post by CorranSW on 2007-04-02
no what i mean is that when i insert the disk i go to the option to continue installation and it just seems to freeze after i click that
ill get a flashing underscore that goes on for hours its the same case with every single OS i have tryed to install

---

### Post by CorranSW on 2007-04-02
from fedora core 6 how do i access a hard drive tool the G parted thing were is that located?

---

### Post by mac.ryan on 2007-04-02
Hi CorranSW, I understood that the ubuntu LiveCD freezes, but what about the windows installation CD? If that doesn't freezes, the easiest, as suggested by some other user above, would be to start the windows installation and simply choose the option to repartition and reformat the hard drive from there (I assume this is an option on M$ installations as well...).

At the very worse, you can try with some other boot CD's like [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) (but there are several other of these CD around...)

---

