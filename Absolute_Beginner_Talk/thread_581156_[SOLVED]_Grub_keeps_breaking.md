---
title: "[SOLVED] Grub keeps breaking"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by wobat on 2007-10-19
I'm dual booting Ubuntu and Windows XP, using Grub.

Everything worked fine until recently, but now running windows breaks grub.

Grub launches windows perfectly, but after it is shut down grub doesn't run at all.
On startup I get a message saying "Grub loading stage1.5.", then it restarts the computer.
The only way to get anything to work is by using a LiveCD.

I've tried following the instructions here...
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
This makes grub run again so I can use ubuntu, but it breaks again if I run windows.

Please help
Thanks

---

### Post by Sef on 2007-10-19
Try reinstalling GRUB with the [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by wobat on 2007-10-19
Billiant! Worked perfectly!
Thanks :)

---

### Post by wobat on 2007-10-21
Spoke too soon.
Grub has stopped working again :(
It's doing the same thing as before.

---

### Post by Sef on 2007-10-21
Sounds like your windows is corrupted.   Other than reinstalling I m not sure what else there is to do.   Hopefully someone else can suggest a less drastic idea.

---

### Post by ronmarley1 on 2007-10-21
I had the exact same issue.  Below is a posting I made to another person having the same issue as you.  The Geocities link below has the solution that worked for me.

I had the same issue. Just about every time I booted windows, GRUB would get corrupted and I'd have to restore using the Super GRUB Disk. In my case, I think the problem was TrendMicro on the Windows side not liking GRUB on the MBR. I finally found this thread on the forums:
[http://ubuntuforums.org/showthread.php?t=469243](http://ubuntuforums.org/showthread.php?t=469243). The thread had a solution found at [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) which worked for me.

---

### Post by wobat on 2007-10-21
Grub is currently installed in the MBR, how do I put the windows boot loader back?

---

### Post by ronmarley1 on 2007-10-21
> **wobat said:**
> Grub is currently installed in the MBR, how do I put the windows boot loader back?

There is an option to restore the Windows boot loader in the Super GRUB Disk.  That is what I used.

---

