---
title: "No CDRW found, strange problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2007-04-23
Ok, something very strange going on with my clean kubuntu install, when I load k3b it says no CDRW found, and theres nothing in /dev, but If I restart, and boot up with a cd in the drive (seemingly anything will do) then It all works as expected, I can burn cds. If I reboot, and load up with no cd, then I can't use the CDRW drive again!
I can only assume something odd is happening when the kernel scans the hardware, but I haven't the foggyest what it could be. Any ideas?
thanks

---

### Post by leibowitz on 2007-04-23
I don't think it's related to the kernel, but maybe just to K3B. If I remember correctly, it needs you to configure it one time to set the device permissions or something similar.

Anyway I don't use K3B anymore so I can be wrong. Did you try with Nero 3beta or something else to see if you encounter the same problem.

---

### Post by richardward101 on 2007-04-23
Its definitely not k3b because when I boot with a cd in the drive then /dev contains both /dev/cdrom and /dev/cdrw, neither of which are there when I boot without a cd in the drive. Also when I boot up without the cd it takes about 10 times as long to boot as when I boot with it. Next time I'm where I can restart it I'll turn off splash and quiet and see if there are any errors, or see where it slows down.

---

### Post by leibowitz on 2007-04-23
Alternatively you can check you logs.

System > Administration > View system log (or something called like this).

You may find what you are looking for.

Anyway, are you sure it's well connected. And check your BIOS aswell if you are not sure about your configuration. I'm not sure that it can't produce that behaviour but who knows.

---

### Post by Phlosten on 2007-04-24
I fixed a few issues by installing a newer version of K3B which is available from their website. There is mention on their website about a few bugs that have been fixed with the 1.0.1 release. For me it is working much better. I couldn't blank DVD's or burn, was really annoying.

The new version has to be built from source unless anyone has a package around?

---

