---
title: "Failed triple boot."
date: 2008-05-29
forum: Apple Hardware Users
---

### Post by blik on 2008-05-29
I am trying to get a working triple boot on a MacBook Pro.

Obviously I started with OSX Leopard.

I made partitions for Linux, and Windows, installed Windows XP on the third partition and after a few tries got it to work.

Yesterday I tried to install Ubuntu (HardyHeron) on the middle partition and it seemed to go well with no real surprises.  It did not give me a chance to make choices on the boot loader though. It is my understanding that whichever one I choose I need to install it to the partition.

When I restarted rEFIt recognized all three operating systems, but when I try either Ubuntu or Windows now I get a black screen saying that it is not bootable.

What do I need to do in terms of repair to make XP run again.  When I installed it the Linux partition was not shown as active, so the third partition was the C drive, now when I go to repair windows is on the D drive.  Is it possible to switch them back or just repair windows?

And from there what do I need to do to get Ubuntu up and running.

Thank you.

---

### Post by cyberdork33 on 2008-05-29
> **blik said:**
> I am trying to get a working triple boot on a MacBook Pro.
First, follow install instructions here:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

and depending on what version Macbook Pro you have, there are specific fixes for hardware in the corresponding Wiki Page:
[https://help.ubuntu.com/community/MacBookPro/SantaRosa]("https://help.ubuntu.com/community/MacBookPro/SantaRosahttps://help.ubuntu.com/community/MacBookPro/Penryn")
[https://help.ubuntu.com/community/MacBookPro/Penryn]("https://help.ubuntu.com/community/MacBookPro/SantaRosahttps://help.ubuntu.com/community/MacBookPro/Penryn") 
> **blik said:**
> When I restarted rEFIt recognized all three operating systems, but when I try either Ubuntu or Windows now I get a black screen saying that it is not bootable.
There is a bug in the Hardy Installer that wipes out the MBR. You can use rEFIt to resync the partition tables. [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by blik on 2008-05-30
I read the items you had posted, and started with the simplest fix first.

Using rEFIt to re synch the drives worked wonders.  Mostly.

When I try to get into windows it hangs up on the grey screen.  When I try to go into Linux I get the grub selections and windows is there.  Both Windows and Linux work from grub.  So everything works and as all I will really use Windows for is games I really do not care how I get to it.

The OCD part of me wants to see it all available from rEFIt though.

Is there a simple fix that will let windows boot from rEFIt?  If not I will live happily this way.

Thank you.

---

### Post by fender177 on 2008-05-30
> **blik said:**
> 
Is there a simple fix that will let windows boot from rEFIt?  If not I will live happily this way.

Not as far as I know.  If you were to load linux and windows on a vanilla PC, a boot loader has to be chosen in order to boot either operating system. Grub installs itself as that boot loader/picker.  Refit is doing essentially the same thing, however, it drops you into the "pc" boot loader, which happens to be grub.

---

### Post by blik on 2008-05-30
Thank you.

As I said I am very willing to accept functional but not elegant.  If there is no simple solution I am good with that.

---

### Post by cyberdork33 on 2008-05-30
> **blik said:**
> Thank you.

As I said I am very willing to accept functional but not elegant.  If there is no simple solution I am good with that.
try fixmbr on the windows recovery disc. That should reinstall the windows bootloader into the MBR. If that wipes out grub then you need to reinstall grub to the Ubuntu partition.

See the Multi-boot link in my sig that discusses the issue and shows you how to change it.

---

