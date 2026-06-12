---
title: "VMware - VMware Display Adapter DRIVER"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by kenweill on 2005-12-29
I have just installed Windows XP inside Ubuntu using VMware Player.

I have also tried installing Bayanihan Linux inside Ubuntu using VMware Player.

During bootup of Bayanihan, it detected that It has a VMware video adapter.

If ever, I want to install Windows 98, where can I get this VMware video adapter driver? In Windows XP, it will automatically adjust its resolution. Even if it the driver for the adapter is not detected or cannot be installed.

Where can I get this drivers?

The drivers that came from my computer will not work when Windows is inside VMware Player.

Its something like VMware Player has its own driver.

(Sorry for my English)

---

### Post by mango.muncher on 2006-09-17
As far as this newbe figures....
Yes VM has its own virtual display driver, it acts as a interface between the  guest machine and the host machine, they use a basic default driver to avoid conflicts.
Vmware creates a virtual box and in this virtual box is are the virtual drivers.
Im running a XP VM guest on Ubuntu. Monitor is LCD 19" The display driver that VM is using for the XP guest produces a low quality res inside the XP window. Im seeking a way to up the VM driver specs so that the guest visuals are better.

---

### Post by sawjew on 2006-09-18
You need vmware tools.  It provides a display driver which will adjust itself to suit your window size and some other features such as copy and paste from host to client etc.  It installs easily in vmware server by just selecting 'install vmware tools' in the menu.  I am not sure how to install them. if you can, in vmware player.  Just google for vmware tools and see if you can download and install them.

---

