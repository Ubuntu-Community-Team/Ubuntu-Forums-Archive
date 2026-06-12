---
title: "Old G3 blu/wht- New Ubuntu"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by dennymoose on 2008-04-30
I got the G3 running yesterday after several attempts. Had to move the Mac OS to an external SCSI drive so I can just leave it powered off, forcing it to boot from internal IDE. Had hoped to have both on external SCSI but Ubuntu doesn't seem to boot that way. (this is the G3 version with both native IDE and bootable SCSI) Had strange experience with internet. To begin with I could log on to my router setup page, but could not access the WWW. Today, after changing nothing, it decided to work. **My question- software updates came up automatically and says there are 202 updates I can download. How do I choose the ones I need, or should I just say yes to all?**
:guitar:

---

### Post by DirtDawg on 2008-04-30
> **dennymoose said:**
> I got the G3 running yesterday after several attempts. Had to move the Mac OS to an external SCSI drive so I can just leave it powered off, forcing it to boot from internal IDE. Had hoped to have both on external SCSI but Ubuntu doesn't seem to boot that way. (this is the G3 version with both native IDE and bootable SCSI) Had strange experience with internet. To begin with I could log on to my router setup page, but could not access the WWW. Today, after changing nothing, it decided to work. **My question- software updates came up automatically and says there are 202 updates I can download. How do I choose the ones I need, or should I just say yes to all?**
:guitar:

The short answer is, let them all install. 202 seems like a lot unless you are using an older version of Ubuntu, but the updates shouldn't hurt anything.

---

### Post by stream303 on 2008-04-30
> **dennymoose said:**
> Had to move the Mac OS to an external SCSI drive so I can just leave it powered off, forcing it to boot from internal IDE. Had hoped to have both on external SCSI but Ubuntu doesn't seem to boot that way.

Usually this means that you have to manually edit your /etc/yaboot.conf file on the external drive, and boot from it while holding down the Alt/Option key to choose it specifically.

In fact, this is a good way to go for those who want to dual-boot, but don't want to mess around with manually editing yaboot.conf.  I have an install of 10.4x on an external firewire, and Ubuntu is on the internal drive - I just choose which to boot from at power-up holding down the alt/option key.

> To begin with I could log on to my router setup page, but could not access the WWW. Today, after changing nothing, it decided to work.

Odd.  While you are in there, if you are running dhcp, you may want to put your isp's primary and backup dns server addresses inside the router's setup page.  In my case, I use the addresses seen on the bottom right page of [www.opendns.com](www.opendns.com).  Putting the addresses inside the router itself works very well if for some reason your machine can't get dns resolution reliably.

Glad to hear a B&W up and running!

---

