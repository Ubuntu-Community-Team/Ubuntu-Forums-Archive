---
title: "PPC ibook HDD Problems"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by sethwoodworth on 2007-04-27
Hi, I have a last generation ppc iBook that I think I hosed the main partition of.

Verbose startup halts on checking disk
 invalid sibling link (4, 8073)

I followed
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2)
tutorial, and got a (hopefully) working usb boot disk working?  I highly doubt that it will work on ppc, but I thought it might give me something to go on.

I don't need an awful lot of hand-holding.  If I could be pointed in the direction of a ppc boot disk and a how-to on how to fix a hfs+ I could probably make my way from there.  Is there any linux OSS software to repair a hfs disk?

So what do you recommend being my first step?

---

### Post by sethwoodworth on 2007-05-06
Ok, I am so lost on this I have no idea.  I successfully put my ibook into target firewire mode, and attached it to another machine, found it as being named disk2s3 (3 being the operative partition).  I tried sudo fsck_hfs and regular fsck.
  fsck_hfs -r /dev/disk2s3
comes back with invalid sibling link (4, 8073), which was the problem in the first place.

[http://www.macosxhints.com/article.php?story=20070204093925888](http://www.macosxhints.com/article.php?story=20070204093925888)

This link looked it had the same problem as me, but I guess that it didn't.

Can anyone give me some ideas here?  Why can I boot ubuntu and read from my disk, but not be able to fix it so it will boot.  Do I need to rebuild the mbr, where should I go from here?

I am really lost on this one.

Is the machine a loss, should I just save all of my media elsewhere and try to backup the /home ?

---

