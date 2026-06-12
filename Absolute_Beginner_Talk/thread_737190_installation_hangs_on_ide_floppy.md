---
title: "installation hangs on ide floppy"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Frequent Modulation on 2008-03-27
First, just wanted to say thanks to all that develop and support Ubuntu. I hope to be using it real soon.

This is my first crack at Linux anything, so please bear with me. 

installing **ubuntu-7.10-server-i386 ** on an Acer Travelmate 213TXV currently running Windows XP.

My issue is the installation 'stops' while detecting hardware. At 84%:

*Loading module 'ide-floppy' for 'Linux IDE floppy'...*

Searching the forums I noticed that this issue was associated to a prior dual boot install by one user. This is not the case as this is the first install of a second OS.

Funny thing is, I dont need the floppy (afaik). Is there a secret Linux code I can type in at the error message to have it bypass the detection of the floppy?

Any help will be appreciated.

---

### Post by dstew on 2008-03-27
Are you installing from a Live CD, or Alternate Install CD? Did you check the CD for integrity (menu item at the start)? The floppy message may not be a true reflection of what the problem is. It might just happen to be what is showing when the real problem occurs. Anyway, if the CD integrity is good, there might be kernel options (secret linux code!) that can get you past the freezing point. Post back if your CD checks out.

---

### Post by kellemes on 2008-03-27
> **dstew said:**
> Are you installing from a Live CD, or Alternate Install CD?

He is installing server edition..

@op
Have you tried with a floppy in the drive? Just a thought..

---

### Post by rkd on 2008-03-27
I don't know whether the server install has this option, but on the desktop versions, the initial menu that appears after booting has a way to let you specify some boot options.   Some of those options turn off or change things it does during booting.

This is described at [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Select this option by pushing F6 from the boot menu, and a line will appear near the bottom of the screen that already has some options on it.  You'll add one or more options to the end of that line.  At this point, F1 will display the names of the options, in case they are different than what was listed in the article linked to above.

noacpi and noapm are two options that sometimes help in situations like you have.  If one or both of them don't fix the hang, try some of the others.  

When you've decided which option(s) you want to try, get out of the help screen and type in the option(s) you want to add.  Then press Enter to let it boot.

If this lets you get past the hang, your problem may be over and subsequent boots from the hard disk after Ubuntu has been installed will work fine.  But sometimes you'll have the same problem again on booting from the hard disk.  In that case, you might have to edit the Grub menu to add the same option(s) to Grub's menu.lst file.  To do that while booting from the hard disk, see the directions on the above linked page under the heading "For Installed Systems That Need Adjustment".  And when you've gotten Ubuntu booted this way, follow the directions at the end of that page under the heading "Permanent changes" to change the Grub menu to include those options permanently.

If your Grub menu gives you the choice among several kernels, you probably will have to add the same options for all of them.

If you have to change the Grub menu, it would be a good idea to make note of what options you added so that if you have to do a complete, from-scratch install sometime later, you will know which options you ended up using in the Grub menu.

---

