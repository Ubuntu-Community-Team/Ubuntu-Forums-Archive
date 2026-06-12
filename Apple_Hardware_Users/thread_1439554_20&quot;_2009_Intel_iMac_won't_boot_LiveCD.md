---
title: "20&quot; 2009 Intel iMac won't boot LiveCD"
date: 2010-03-26
forum: Apple Hardware Users
---

### Post by Firepowerforfreedom on 2010-03-26
Hi all, in an attempt to demonstrate just how compatible our college Macs are (please hold the tomatoes) I'm trying to install Ubuntu Karmic alongside Mac OS X Leopard and Windows XP Pro SP2. The problem is, I hold down 'C' to boot from the CD, and all I get is a black screen with a flashing DOS-style cursor. If I boot it without holding C, it works just fine, booting into either Mac or Windows (whichever I specified).

This is understandably irritating, and I'm trying to figure out the source of the problem. Any thoughts?

---

### Post by linuxopjemac on 2010-03-26
try this:
[http://test.ubuntuforums.org/showthread.php?t=1304923](http://test.ubuntuforums.org/showthread.php?t=1304923)

---

### Post by Firepowerforfreedom on 2010-03-26
Sorry. Let me clarify: I know what the Ubuntu CLI looks like, but it won't even get me that far. No boot action whatsoever.

---

### Post by jamesey on 2010-03-26
i have imac model 9,1 from march 2009
I just hold down the option button when i boot and the cd just runs and does it's thing.

---

### Post by bandrak on 2011-08-22
I've got the same problem.  Something went wrong with my iMac during an update and it won't boot.  I can boot from the Mac OS X disk I have, but refuses to fix anything with that unless I format it and erase everything (since the Mac has snow leopard and that's newer).

As I am trying to get a snow leopard CD to fix it I tried using an Ubuntu Live CD to do a back up.  After telling the mac to boot from the CD it goes into a black screen with only a white '_' going on and off (not really booting).  My iMac is from also from 2009 or 2008.

---

### Post by nkassi on 2011-08-23
I've just installed it on my laptop. If you have a Nvidia card like I do it will hang when the nouveau drivers try to boot. You need to edit the boot options on the live cd. Press F6 and at the end of the kernel line add nouveau.noaccel=1 

It should boot now. There is a way to tell the system to install the restricted drivers during install but I can't remember where it's at in the installation process so if you can't find it, on next boot when you see grub press e while on the line for ubuntu and add the nouveau.noaccel=1 to the end of the kernel line. (not initrd, I believe it's second from last). 

Hope that helps.

---

