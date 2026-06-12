---
title: "core duo macbook pro sleep problem"
date: 2008-02-01
forum: Apple Intel Users
---

### Post by sjatkins on 2008-02-01
I read somewhere that there is a fix for this machine not sleeping properly under gutsy.  The only fix I have been able to find after search altogether too long is to roll back to an earlier version of the kernel.   I would rather not do that.  Is there a patch or forward fix?  I also don't know if the rolling back actually will work or what else I may lose.  If there is a known problem with the current version isn't there a patch somewhere?   If I can't solve this to my satisfaction I probably won't run ubuntu on this machine except under <gag> virtualization.  Which would be a shame.   So any help much appreciated.

---

### Post by wahr on 2008-02-01
This is relevant to my interests.

I've had complete inconsistency with sleep on the current kernel, and the only docs i've seen say to roll back.

I'd very much like to avoid this if possible.

I'm currently at the initial install phase though, so I have a clean, risk free system to play with. :guitar:

I'll give you feedback on how the kernel rollback works.

Edit: the rollback worked flawlessly and was very painless. Install 5 packages in a specific order, run kate in root to alter a line in a config file, and youre up and running.  No need to tiptoe on the updates either because of the way the boot config works : )

---

### Post by cyberdork33 on 2008-02-01
Do you have ATI graphics? The Linux kernel changed how it handles memory allocation, and ATI did not fix their drivers until just recently. The very latest driver release (fglrx) will suspend, but there are some other problems with it. 
[http://ubuntuforums.org/showthread.php?t=671235](http://ubuntuforums.org/showthread.php?t=671235)

---

### Post by chlee on 2008-02-01
yep! 

im using an ATI and sleep will not wake up. boo! im reduced to shut down to roam with the laptop.
:lolflag:

 im on the lookout, if post if i find anything..

---

### Post by prana on 2008-02-01
I have a core 2 duo macbook pro 2.16 and I had to upgrade to the 2.6.24 kernel from Hardy to get suspend to work.

Don't know if this will work on the core duo macbook pro but here goes...

You should start off with this guide:

[https://wiki.ubuntu.com/MacBookPro]("https://wiki.ubuntu.com/MacBookPro")

In this guide, before you try to install the ATI driver, you should upgrade the kernel

The post showing how to do that is here:

[http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755")

Once you upgrade the kernel, follow the steps in the Wiki guide to get the rest of the components working.

Also, to suspend,I had to change the following in /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false 

Good luck!

---

