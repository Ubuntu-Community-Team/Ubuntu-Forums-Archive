---
title: "Missing Desktop Icons for mounted Network"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Mad Gerald on 2007-10-06
Hi I'm a newbie to this so please bear with me

I have recently changed from 7.04 32 bit to the 64 bit version. This worked fine in the 32 bit version.

I have a simple home network with 1 Ubuntu machine & 1 XP machine

I mount the XP machine using 

sudo mount -t cifs //192.168.1.4/C /mnt/imedian_c -o user=MEDIA_PC

But the icon doesn't appear on my destop or in my places menu.

If I browse direct to the mnt/imedian_c folder the contents can be accessed.
Network also appears in Places-Network

I've tried
gconf-editor 

and followed instructions as per
[http://ubuntuforums.org/showthread.php?t=421266](http://ubuntuforums.org/showthread.php?t=421266)

still no icons appear.
Other Icons for mounted harddisks etc do appear. So is the there a special icon used for a mounted windows network that I'm missing.

Any help would be apreciated

Thanks

Shayne

---

### Post by chrisxp on 2007-10-08
you could try mounting it to '/home/<user>/Desktop'

maybe that would work

---

### Post by Mad Gerald on 2007-10-09
Yes that works but I have the Icon there all the time
I really only want the Icon when it is mounted

---

