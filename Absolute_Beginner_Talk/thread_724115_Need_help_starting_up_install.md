---
title: "Need help starting up install"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by HitRefresh on 2008-03-14
I'm trying to install Gutsy on a HP DV6704nr laptop. I've tried installing directly from the Live CD --> "Start or install Ubuntu" , but that gave me an error of "Can not find screen or graphics card" or something. 

I've also tried just booting into safe mode and then clicking on "install" icon - but the install dialog was too big for the screen, and I could not change the resolution successfully either in safe mode. I've tried the Alt CD but I'm not advanced enough to use it, yet. I'm stuck when it says to select "storage disk driver" ? I don't want to mess up the running Vista, yet.

Thanks for any help.

---

### Post by chlorinekid on 2008-03-14
what graphics driver does your laptop use?? do you know?

---

### Post by aeiah on 2008-03-14
the easiest thing to do would be to install from the text mode (alternative cd).

its really pretty simple. the only bit which may be daunting is the partitioning. you can do the partitioning before installing my using the gparted livecd. this uses a graphical environment and is the same partitioning program that ubuntu uses. you should be able to see what you're doing with that, partition the hdd accordingly, and then reboot with the ubuntu alternative cd. 

make sure you read a howto for installing ubuntu dual boot with vista present though, of course

---

### Post by Sef on 2008-03-14
To dual boot with the alternate cd, read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by HitRefresh on 2008-03-14
Thanks. I will use gparted first to do the partitions. Yeah, I'd rather use the alt CD to install.

I was stumped when using the ALT CD at the step "Detecting disks and other hardware" - which I think Ubuntu did not detect on the laptop, but then brings up a big list of disk drives (i think) ? 
I don't know which one to select here. Thats where I got stuck.

The laptop has  a 160GB Serial ATA hard drive. Shouldn't Ubuntu detect the drive, the same way that the how-to does ? I don't know much about that step. Maybe doing the partitions first with gparted will remedy this ?

---

