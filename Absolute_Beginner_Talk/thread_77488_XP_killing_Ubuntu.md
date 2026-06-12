---
title: "XP killing Ubuntu?"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-10-16
So i've got Ubuntu 5.10 up and running without any problems.  Anyway, I'm wanting to dual boot with XP, however, the only info i can find on this suggests installing unbuntu with XP already installed.  I've got a 20 gb fat32 partition on hda1 than i plan on using for XP.  Is this as easy as using gparted to repartion that to a ntfs filesystem and simply booting up with cd?  Is there another easier route to getting this done?  Also, i wouldn't mind installing Ubuntu again, as practice with this can only do good for me.

---

### Post by aysiu on 2005-10-16
Windows XP will kill Grub, but that's not a big deal. Install XP, then follow [these directions for restoring Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Hobbsee on 2005-10-17
Yes, you've got it the right way, and probably in the simplest order :)

Practice is good...but too much practice is a pain, although it does let you do it almost without thinking...

---

### Post by Griff on 2005-10-17
Cool.  Just one little snag i've come across however.  When trying to convert hda1 from fat32 to ntfs using gparted i get an error message.  This is followed by the hda1 partition going from a fat32 to 'unknown'.  Is there a mounting problem here or what?  I can take it back to fat32 but can't seem to get to ntfs.:confused:

---

### Post by Griff on 2005-10-17
Think i'm going to try to use the install disc to change that filesystem, since gparted is encountering some problem (error between keyboard and seat? lol).  For those that might be having a similar prob i'll post what happens using this method.  All this is still alien to me, but you know what, i don't care.  Having fun learning. :p

---

