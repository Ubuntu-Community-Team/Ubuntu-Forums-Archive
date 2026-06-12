---
title: "[SOLVED] About ready to split my skull open: Problems with iTunes and bootpoints"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Knoll318 on 2007-12-31
I have been having so many problems, it's getting very agitating.  Perhaps you people can help:

I installed Ubuntu with Wubi and mounted it onto a separate partition which I cut off of free space from my Windows partition in Gparted.  Let me show you a crude diagram of what my partitions should look like:

[IMG]http://i48.photobucket.com/albums/f212/Kratos318/shouldbeharddrive.jpg[/IMG]

Pretty crude, but the job gets done.

Instead, in Gparted, my NTFS shows a warning symbol and says it can't find the bootpoint, or mountpoint, I can't remember.  So my hard drive looks like this:

[IMG]http://i48.photobucket.com/albums/f212/Kratos318/isharddrive.jpg[/IMG]

Okay, so I got worried when I saw that, so I decided to open up Windows.  Everything is fine in Windows, except when I try to open up iTunes or Quicktime it says there was an error and it eneds to shut down.  I can try a hundred times and get the same result.  So, I try to uninstall both Quicktime and iTunes, and it works.  But then I try to install them, and the installer for Quicktime gets to the point where it deletes old files, then the bar goes back.  Same if I try the iTUnes+Quicktime installer.  If anyone can help me, that would be great.

---

### Post by spiderbatdad on 2007-12-31
not sure whats going on here. Did you defrag the windows partition just prior to installing ubuntu?

---

### Post by yaknowwat on 2007-12-31
If you still have your windows install CD then do this.

start from it go to the Repair console
then use this command


chkdsk /?

This is give you a munch of option available look for the flag that forces check and repairs if needed.
(reason I say his is i cant remember that flag off hand.)

chkdsk C: /FLAG's

If that doesn't help any (or cant find install CD)

use testdisk on ubuntu (you can find in the synaptic package manager.)

start testdisk via terminal.  Its pretty easy to use maybe that can repair windows for you.

---

### Post by zipperback on 2007-12-31
If you want to create a dual boot system check out these links.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

The following link has several different tutorials which deal with dual booting.
Linux, XP, Vista, etc.....
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)


You might be better off doing a full backup of all your valuable files, and then building a dual boot system from scratch.

- zipperback
:popcorn:

---

### Post by Irihapeti on 2007-12-31
Something that used to happen to me when I ran a dual-boot system.

If I had Gparted installed in my Ubuntu system and used it to look at my NTFS partition, I got the same thing - the warning and the triangle. If I used the Gparted liveCD to boot and looked at the NTFS partition - no problem.

You don't say if you are using a liveCD. If you aren't, maybe you are having the same problem. The liveCD is available here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Knoll318 on 2007-12-31
I'm not using a LiveCD, and sadly, I'm out of CD's, so I can't burn anything.

---

### Post by Knoll318 on 2008-01-01
Luckily I figured it out, so everything is fine with iTunes now.

---

