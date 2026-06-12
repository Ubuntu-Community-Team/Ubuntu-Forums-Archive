---
title: "Mac OS X installation problems"
date: 2007-11-10
forum: Apple Intel Users
---

### Post by God of the Meeps on 2007-11-10
I'm trying to install Mac OS X from Feisty, but there was an error message that said that it couldn't mount it, so I tried rebooting then holding the ALT key until it went to the boot screen and selected the Mac OS X CD. I did the steps, until it came to the hard drive selection screen, where there were no hard drives to be selected.

---

### Post by aysiu on 2007-11-10
What do you mean you're trying to install it "from Feisty"?

Do you currently have Ubuntu installed as your main OS on an Apple computer, and you're trying to install Mac OS X through VirtualBox?

---

### Post by God of the Meeps on 2007-11-10
Ubuntu is my main operating system on an Intel Mac.

---

### Post by God of the Meeps on 2007-11-10
Oh, and I'm trying to install Mac OS X normally.

---

### Post by warmwaddle on 2007-11-10
Is it an external Hard Drive you are trying to use?

---

### Post by God of the Meeps on 2007-11-10
No, the hard drive is internal.

---

### Post by Sorivenul on 2007-11-10
> **God of the Meeps said:**
> Oh, and I'm trying to install Mac OS X normally.
So you only have Ubuntu on your machine?

If this is the case, the partition table is probably in the wrong format.  OS X relies on a GUID partition table to install, but boots just fine from an MS-DOS partition table or any other you may have Ubuntu set up on.

---

### Post by cyberdork33 on 2007-11-10
> **Sorivenul said:**
> So you only have Ubuntu on your machine?

If this is the case, the partition table is probably in the wrong format.  OS X relies on a GUID partition table to install, but boots just fine from an MS-DOS partition table or any other you may have Ubuntu set up on.
Yea, you have to have a GPT.

You can install OSX to a an external drive, then clone it to an internal HFS+ partition as it doesn't check the format type except when installing.

---

### Post by God of the Meeps on 2007-11-11
Okay... so, that means that I can't install Mac OS X unless I'm using an external drive?

---

### Post by Sorivenul on 2007-11-11
> **God of the Meeps said:**
> Okay... so, that means that I can't install Mac OS X unless I'm using an external drive?

Yes, from my knowledge.  Or unless you would do a full wipe and reinstall of OS X on your main drive, but most wouldn't want to take that drastic of a measure.  However, if that's the path you take, obviously back up your other data to an external drive first.

---

### Post by God of the Meeps on 2007-11-11
I really don't have a problem with using a full wipe, but I can't install Mac  OS X (and don't have an external drive)

---

### Post by Sorivenul on 2007-11-11
If you want to install OSX and Ubuntu and are okay with doing a full wipe, then do the wipe.  Here's what I did:

1.)  Insert OSX install media, there's your normal Finder menu at the top of the screen after you get past the initial setup phase. From there you can find the good old Disk Utility.
2.)  Use Disk Utility to format/partition your drive as you see fit.  Don't worry about partitions for swap or Ubuntu yet.  Once done, your disk should be back to an OSX installable GUID partition table.  
3.)  Install OSX.
4.)  When OSX is done installing and you're satisfied that it runs

If you want to choose your OS using a utility like rEFIt, install rEFIt or whatever you choose before you continue with step 5.

5.)  Insert your Ubuntu install CD.
6.)  Use GParted or the partition editor in the installer to set up your Ubuntu partitions.
7.)  Install Ubuntu.
8.)  Rejoice!  You now have fresh installs of OSX and Ubuntu.  

GOOD LUCK!

---

