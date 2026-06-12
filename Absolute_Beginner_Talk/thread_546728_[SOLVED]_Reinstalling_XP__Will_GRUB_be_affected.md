---
title: "[SOLVED] Reinstalling XP:  Will GRUB be affected?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-09-09
I need to reinstall XP on my dual boot system, it's falling apart, will it affect GRUB/Ubuntu in any way?

Is it possible from the XP installer to choose a specific location to put it?

---

### Post by vanadium on 2007-09-09
Grub will be destroyed. This is the way how XP works. However, it can be reinstalled easily afterwards.

---

### Post by erfahren on 2007-09-09
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://ubuntuforums.org/showthread.php?t=312940](http://ubuntuforums.org/showthread.php?t=312940)

I guess you may have already found them.

---

### Post by bobpur on 2007-09-09
XP will overwrite GRUB. To do it right, you will have to install XP first and then install Ubuntu last. 
An XP install last will tend to overwrite GRUB rendering Ubuntu (or any distro) inaccessible.
Anyhow, to the best of my knowledge, this is how it works.

---

### Post by aberadam on 2007-09-09
Great, thanks a lot.  

Gotta do some research...

---

### Post by regomodo on 2007-09-09
the very 1st item from a google search of "restore grub"

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

helped me out a couple of times

---

### Post by aberadam on 2007-09-09
After looking at this, it seems easier just to wipe the lot and reinstall Ubuntu.  I'm sure I'll mess something up and end up losing all my Ubuntu stuff.  Not worth the risk. 

I'll wait until Gutsy's out and then reinstall both.

---

### Post by samkline on 2007-09-09
you don't need to do that, it is very easy to restore grub. after installing windows XP, boot off the ubuntu liveCD, and follow the instructions on this page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by aberadam on 2007-09-09
It's this I'm worried about: 

> You will get a grub prompt. We will use tab completion to find your root partition and install grub to the MBR (hd0,0)

    *

      <tab> = hit the Tab key : This will return your root partition, something like root (hd0,1). Hit the <Enter> key and continue.
    *

      If you do not know your boot partition, use find /boot/grub/stage1



Root partition?  What's that?

---

### Post by aberadam on 2007-09-09
OK, I did it, I used Super Grub Disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/))

When done just popped the disk in and followed the well-explained menus.  No command line typing!

---

