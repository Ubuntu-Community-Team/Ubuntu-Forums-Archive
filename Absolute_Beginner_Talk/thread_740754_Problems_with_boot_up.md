---
title: "Problems with boot up"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Jimmy9pints on 2008-03-31
I previously installed Ubuntu to try it out and I really liked it. However, I experienced boot problems that ultimately lead to me (against my will) going back to windows.

I have been keen to get rid of Windows for a long time - ultimately I would like to use opensource in all my home and business operations...but first I have to learn it myself, hence my keeness to try again.

Anyway, on to my question:

Last time I tried to have a dual boot system, Ubuntu and Xp. The problem was, that after I installed Ubuntu and tried to reboot I got a NTLDR missing error. Then, by chance, I tried to reboot with the XP CD in the drive - it loaded grub and I had the choice of the two operating systems and I could happily boot either OS. If I ever took the CD out, it would not load grub and I could not boot either OS. I thought it very odd.

Then, I tried using the windows CD to load the recovery console and entered a FIXBOOT command. Upon rebooting it logged straight into Windows and Ubuntu was never to be seen again...

Anyway, here I am again trying to use Ubuntu. Because apart from this glitch I was happy with Ubuntu, I totally got rid of windows and installed a single boot system. However, I still have the same problem. It will not boot up unless the windows CD is present - sorry I can't remember the error message it gives me this time. But in anycase, the Windows CD loads grub and it automatically loads Ubuntu.

thanks....

---

### Post by Malta paul on 2008-03-31
Hi, Running the Windows recovery would zap Grub from your master boot area. Its always best to have Windows installed first and then install Ubuntu. That way the Grub menu will configure Ubuntu and Windows to run on your HD boot sector. If you have no Ubuntu files you need or have them backed up, just install Ubuntu again from the live CD. If you have Ubuntu files you need, run the live CD and back them up first before installing Ubuntu to your HD.
This may help:[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Have fun :)

---

