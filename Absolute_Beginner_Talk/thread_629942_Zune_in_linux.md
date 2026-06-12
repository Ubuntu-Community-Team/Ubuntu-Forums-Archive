---
title: "Zune in linux"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-02
Has anyone been able to get a zune to transfer songs onto a linux machine yet? will WINE work

---

### Post by Delvien on 2007-12-02
> **Dapman01 said:**
> Has anyone been able to get a zune to transfer songs onto a linux machine yet? will WINE work


Zune, because its microsoft, can only work on a windows machine, because of the specialsupersneaky handshake it has to do to verify a valid install of windows. 

I think its possible with a Vmware virtual machine though.

---

### Post by daengbo on 2007-12-03
This is not exactly the #1 method to do it, but you should be able to run WindowsXP inside VirtualBox and connect via the USB port. I have a video on how to set up VirtualBox in seamless mode.
[http://ibeentoubuntu.blogspot.com/2007/12/running-windows-applications-in-ubuntu.html](http://ibeentoubuntu.blogspot.com/2007/12/running-windows-applications-in-ubuntu.html)

Daeng

---

### Post by daengbo on 2007-12-03
This is going to be a silly question, but I though Zune used MTP, which Rhythmbox supports as a plugin in the newest version. Have you tried turning on MTP and dragging from withing Rhythmbox? I don't have a Zune so please excuse me if this is a known non-working method.

---

### Post by jakep_82 on 2007-12-04
The Zune is MTP, but Microsoft added in extra authentication.  The end result is you can view the contents of the Zune, but transferring to or from the device is not possible.  VirtualBox worked for me, but only if I disabled USB 2.0 (ehci-hcd).  That makes transfers painfully slow so against my better judgment I'm now dual booting for the sole purpose of syncing my Zune.

---

### Post by zed41 on 2007-12-08
what are the possibilies of setting up the Zune through virtual box with the usb to start out. then configure the wireless connection through an ad-hoc connection. wouldn't that bypass the slow usb connection?

---

### Post by onion221 on 2007-12-11
So ridiculous, I'm not buying one now. I bet that move cock blocked a lot of sales.

---

### Post by agibby5 on 2008-04-01
> **jakep_82 said:**
> The Zune is MTP, but Microsoft added in extra authentication.  The end result is you can view the contents of the Zune, but transferring to or from the device is not possible.

That's ridiculous... I'm sure it can be broken/hacked... until then, virtualization it is.

---

### Post by aslamp on 2008-04-15
Could downgrading the firmware for the Zune allow for Rhythmbox to pass through? I haven't gotten my Zune yet, but once I will I'll try it.

---

