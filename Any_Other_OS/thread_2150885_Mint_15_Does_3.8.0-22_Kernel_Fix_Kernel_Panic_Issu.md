---
title: "Mint 15: Does 3.8.0-22 Kernel Fix Kernel Panic Issue with 3.9.0-19?"
date: 2013-06-02
forum: Any Other OS
---

### Post by buzzingrobot on 2013-06-02
Both the new Linux Mint 15 and Ubuntu 13.04 are essentially unusable on my hardware due to kernel panics in the default 3.8.0-19 kernel both distributions use. Crashes happen either attempting to boot the install DVD or at the first boot after the install, and frequently thereafter.

I hear that the 3.8.0-22 kernel fixes this.  Is that correct?

---

### Post by pissedoffdude on 2013-06-02
I had a similar issue booting the latest Ubuntu as well.  It would happen like half of time I tried to boot it.  I ended up installing the linux-pf kernel (mostly because I couldn't find a stirctly ck one) by going here [http://repos.natalenko.name/ubuntu/pf/](http://repos.natalenko.name/ubuntu/pf/). Just download the latest one and make sure you install the headers, image, and source.  Assuming you download them to your Downloads folder, it's is simple as doing a ```
cd Downloads
sudo dpkg -i linux*.deb
```

Or just double click them.  You can probably find a repo for the latest kernel with Ubuntu's patches if you don't want to use the pf patchset as well

Edit: If you want to know if an update via the system updater fixes this, you'll have to post your system specs (be speicifc about your MOBO), as this isn't an issue for everyone

---

### Post by buzzingrobot on 2013-06-02
> **pissedoffdude said:**
> 
Edit: If you want to know if an update via the system updater fixes this, you'll have to post your system specs (be speicifc about your MOBO), as this isn't an issue for everyone

OK:

Gigabyte Z68XP-UD3 motherboard; 16gig RAM
Intel i7-2600k
Nvidia GeForce GTX 550 Ti
Marvell Ethernet Card (ethernet on the motherboard disabled)
4 drives: 3 Hitachi, 1 Samsung

---

### Post by pissedoffdude on 2013-06-02
I couldn't find anything specific relating those specs and kernel panics.  Try updating the kernel as I posted earlier and let us know if that helps.

---

### Post by buzzingrobot on 2013-06-03
Reinstalled, did a dist-upgrade, a 3.8.023 kernel was installed, and that seems to have stopped the panics, so far.

---

