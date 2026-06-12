---
title: "[SOLVED] Ubuntu on External Drive Kernel panic"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nikRbokR on 2008-02-18
So, I installed Ubuntu on my external drive.  I am using a laptop to do this.  Just to be safe, I removed the hard drive from the laptop.  I installed everything and it seemed to work fine.  However, after restart, on loading, it told me something like:
[ *random number*] Kernel Panic: Couldn't mount fs (0

It was something like that (sorry I do not know the exact message).

Could someone please help me?  I'm new to Ubuntu.  One of the problems may be that I have a crappy external drive and it shuts off and turns back on when I move it.  But I made sure to keep it on and connected during the installation, so that's probably not the problem.

Thanks.

---

### Post by Mark_in_Hollywood on 2008-02-18
FIRST: I want you to know that I have never done what you describe. 

But I have had to install/reinstall Ubuntu many, many times.

If you are using Ubuntu v. 7.10 (Gutsy Gibbon), the install would have looked at all your hardware on the computer during the install. (Same for M$, it 'finds' all the hardware).

If you have taken out the laptop drive, and installed software from scratch, so to speak, then putting the drive back in it's original bay has told Ubuntu that the UUID is wrong. It may have done this even if the drive was the exact same make, model, gig size, etc.

There is a laptop / hardware subforum at Ubuntuforums.org.

[http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)

Post there, giving the laptop make, model, specs. If there is a hardware problem, you will know before you install Linux.

Also, google the keywords: ubuntu and your laptop make, e.g. Satellite 1905s304, and the word troubleshoot. If a problem exists, you will know ahead of time as to how to fix it.

Welcome to Ubuntu.

---

### Post by MasterJS on 2008-02-18
In my link at the bottom of my post here, i have a post on that blog that talks how to put ubuntu onto an external hard drive. You do not need to put Xubuntu on it, but follow the rest of the instructions to install Ubuntu correctly.

---

### Post by nikRbokR on 2008-03-23
Well, I found a few other posts that were very helpful.

To fix I:

edited /etc/initramfs-tools/modules
edited /boot/grub/menu.lst

I've done it twice now (first time, it didn't work as well).

Hope others who are attempting to do install to and external drive are successful!
Good luck!

---

