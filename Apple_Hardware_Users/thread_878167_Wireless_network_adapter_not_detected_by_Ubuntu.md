---
title: "Wireless network adapter not detected by Ubuntu"
date: 2008-08-02
forum: Apple Hardware Users
---

### Post by Smacky311 on 2008-08-02
I have a macbook pro Penryn (4th generation).  I followed the directions here: [https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn) .  My wireless does not function.  I go to System > Administration > Windows Wireless Drivers > I see the bcmwl5 driver and it says "Hardware Present: No".  I can't see anything wireless in my network settings either.  

I checked the dmesg log and searched for ndiswrapper and all I got was "ndiswrapper version 1.52 loaded (smp=yes, preempt=no)" and "usbcore: registered new interface driver ndiswrapper"

I just started using Ubuntu yesterday so please don't skip any of the basics.

---

### Post by Smacky311 on 2008-08-02
Does anyone have any troubleshooting suggestions?

---

### Post by cyberdork33 on 2008-08-03
Well that is obviously not the right driver for your machine.

what does 'lspci' give you?

---

### Post by Smacky311 on 2008-08-04
I ran all the system updates for Ubuntu and now my internet works.  My wireless is still not detected, but NAT must be working its magic to let me use the internet of the host operating system.  This works for me for the time being.  Thanks.

---

### Post by cyberdork33 on 2008-08-04
> **Smacky311 said:**
> I ran all the system updates for Ubuntu and now my internet works.  My wireless is still not detected, but NAT must be working its magic to let me use the internet of the host operating system.  This works for me for the time being.  Thanks.
So you are using a VM? That would have been helpful information. You do not need to setup wireless in the VM as it uses the Host's internet connection... (as you have already discovered.)

---

