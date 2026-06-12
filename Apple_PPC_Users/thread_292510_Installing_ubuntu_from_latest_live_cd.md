---
title: "Installing ubuntu from latest live cd"
date: 2006-11-03
forum: Apple PPC Users
---

### Post by tbluhp on 2006-11-03
I am trying to install this on my machine but when I do I get error no bootloader or something? How do I fix it?

Also can it be installed on external drive?

I installed or tryed to from auto install

---

### Post by amohanty on 2006-11-04
One of the options at boot is to test media integrity, run that to make sure that the media is fine.

AM

---

### Post by tbluhp on 2006-11-04
It is fine?

---

### Post by amohanty on 2006-11-04
Do you mean the media (cd) tested ok?
Can you get to the initial menu at all?
What happens when you select Install Ubuntu (first item on the menu)?
Do you get the loading kernel message?

AM

---

### Post by xerman on 2006-11-04
The only way to install ubuntu with no macosx installed is using the ALTERNATE CD. This is the one that allows the creation of the AppleBootstrap partition needed to startup the machine.

Gparted is the HD partition application that the graphical installer of the liveCD uses to create partitions for installation, but does not allow the creation of the AppleBootstrap. So the installation will always fail at this step.

regards

---

### Post by tbluhp on 2006-11-04
I do have macosx installed.

---

### Post by fisherdmin01 on 2006-11-05
Hate to be contrary, but I installed "regular" Hoary from CD w/ no Mac OS.  I know this because I could not install OS X on the little beast - kept saying there was no target drive and I couldn't repartition the drive from within OS X installer.  Grabbed the Hoary disk and hours later, I had a working OS.

Just my experience .....

> **xerman said:**
> The only way to install ubuntu with no macosx installed is using the ALTERNATE CD. This is the one that allows the creation of the AppleBootstrap partition needed to startup the machine.

Gparted is the HD partition application that the graphical installer of the liveCD uses to create partitions for installation, but does not allow the creation of the AppleBootstrap. So the installation will always fail at this step.

regards

---

