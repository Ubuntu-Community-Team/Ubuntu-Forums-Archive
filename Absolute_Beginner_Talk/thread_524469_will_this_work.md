---
title: "will this work?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by tadada on 2007-08-13
Ok I need to get onto a partition to get a few files now my plan so far is to finish installing CLI system and then give it the graphical interface and stuff like I was going to and get the file from there.

But I was wondering if instead I can install the system but tell it to boot from the originnal partition (the one I wat to get on). would it boot the original install of Ubuntu nomrally or would it fail totally and I would lose my very important file?

No redoing said file is not an option this would be better and yes I did backup said file but said file backup died.

---

### Post by jambarama on 2007-08-13
> **tadada said:**
> Ok I need to get onto a partition to get a few files now my plan so far is to finish installing CLI system and then give it the graphical interface and stuff like I was going to and get the file from there.

But I was wondering if instead I can install the system but tell it to boot from the originnal partition (the one I wat to get on). would it boot the original install of Ubuntu nomrally or would it fail totally and I would lose my very important file?

No redoing said file is not an option this would be better and yes I did backup said file but said file backup died.

Let me make sure I understand your question.  You began an install, but need to get a few files off an existing partition, presumably a different partition than you began to install to.  The easiest way to do this I can think of, would be to boot off the Ubuntu install disk, which is also a live CD.  Put in a flash drive.  Ubuntu should automount both your existing partition with the imporant file and your flash drive, as icons on the desktop.  Drag and drop to the flash drive, then do the typical install.    

Alternately you could install Ubuntu to a *different* parition than the file is on, boot into your new system, and Ubuntu should automount the existing partiton.  

Also, no need to install a command line system--Ubuntu has nothing like the Debian net-install disc--the installer will take care of selecting software packages, which would include a window manager.

---

