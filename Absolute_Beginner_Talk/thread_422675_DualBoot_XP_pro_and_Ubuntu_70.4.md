---
title: "DualBoot XP pro and Ubuntu 70.4"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by abduliounited on 2007-04-25
Good Afternoon, 

someone can help me? I would like to install Ubuntu 704 on my laptop which has already installed XP pro SP2. 
is there somebody who can give me some instructions? or do you know where I can find a guide dualboot installation? 

Thanks
tony

---

### Post by LaRoza on 2007-04-25
Doing a dual boot with XP is relatively painless.

You can search the forum guidence, but the easiest way to do it would be to let Ubuntu resize the partition and install itself, XP will automaticall be detected and added to Grub.

---

### Post by BaffledMollusc on 2007-04-25
But if you're going to be resizing the XP partition, defrag the hard drive from within Windows first.

---

### Post by SoundFriend on 2007-04-25
Yes, the installer really should offer the user this advice.  It could be a bit more user friendly.

SF

---

### Post by abduliounited on 2007-04-25
I have only on partition where xp is installed. 
I just need to insert the boot cd and let Ubuntu to do the rest?

---

### Post by doomster on 2007-04-25
yes. just run ubuntu from cd, and selct install from ubuntu desktop. let ubuntu resize partitions, and youre done.
it will, as said above, find windows xp installation, and insert it to boot loader grub

---

### Post by Gina on 2007-04-25
Can I just recommend that you carefully back up everything of any value just in case anything should go wrong.  I've done several installs of Ubuntu with dual-boot without a problem but changing partition sizes can cause problems.  Most important to defrag Windows drive as has been mentioned and a good idea to run a disk test too.  After resizing it's partition, Win XP will want to check the drive next time you boot it - it recognises the change in size.

---

### Post by carlolsen on 2007-04-25
If you want to be 100% safe, simply get a second hard drive (if it's easy to do for your particular laptop).  Then, just swap hard drives when you want to swap OS's.  The only danger to your XP installation is then that you might drop it on the floor.

If you need to share data between the OS's, then an external eSATA or USB drive is very handy.

For those of you non-laptop users reading this forum, I do this on my full-size desktop comptuer by using removable hard drive enclosures from Startech, which cost about $25.

---

