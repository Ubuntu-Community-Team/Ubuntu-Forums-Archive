---
title: "had to install xp can boot back to ubuntu 7.10"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by garifo on 2008-01-02
I had to reinstall XP again on my xp partition and now I cannot access my ubuntu.  When I boot it goes directly into XP.

I booted from the Ubuntu CD and Browse through the hard drive partitions and looked at my ubuntu menu.lst file and it shows there.

How can I fix the loader (boot or grub not sure which one) so that it displays the menu to select the Operating system I want to boot into?
 Ubuntu is my main OS and I have tons of files there that I cannot copy to an external HD due to OS permission so the message says.

I browser through my ubuntu directory on that partition but I am unable to backup those files .


Any help will be greatly appreciated.

---

### Post by Biggy on 2008-01-02
i had the  same problem...

---

### Post by jken146 on 2008-01-02
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by (((X))) on 2008-01-02
there is a way to do so
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

or you can install linux again, so you would nave an option to boot ubuntu..and edit your menu.lst:P

---

### Post by Borbus on 2008-01-02
It's because the Windows installer, unlike any decent linux installer, will not look for other operating systems and just blindly write a new boot loader which will only boot your new microsoft OS. Because you can't possibly be using anything else right?

I would use the super grub disk as detailed in the link jken146 provided.

---

### Post by philinux on 2008-01-02
Or read this if you have the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Biggy on 2008-01-02
> **Borbus said:**
> It's because the Windows installer, unlike any decent linux installer, will not look for other operating systems and just blindly write a new boot loader which will only boot your new microsoft OS. Because you can't possibly be using anything else right?

I would use the super grub disk as detailed in the link jken146 provided.

thank you Borbus 

i download Super Grub Disk [here]("http://forjamari.linex.org/frs/?group_id=61&release_id=499")

---

