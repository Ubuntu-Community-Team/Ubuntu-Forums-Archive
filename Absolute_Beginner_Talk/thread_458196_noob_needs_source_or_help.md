---
title: "noob needs source or help"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by flip_flop on 2007-05-29
I wanted to try a few distros before committing to one however cant uninstall ubuntu or at least grub.
I have tried searching all the forums and "read me"`s but only get one answer everywhere.

I have a dual core 64bit processor on a laptop with OEM vista on it before installing i backed up and defragged but tried to restore system back but it will not work due to a hidden partition on the hard drive.
After lots of research found out third party software on computer and vista security prevents me from restoring if the hard drive configs are changed(It also refuses if you change the dvd - security and copyright protection on vista is way over the top).  If i try the usual fdisk it will trash my ntfs vista doesnt support fdisk any more. During installation of ubuntu a message came up telling me how to remove grub if needed.

Could someone please tell me how i can remove ubuntu with out having to take my laptop back to the shop to have the hard dirve swapped (this is what windows vista tells you to do if you change any hardware).

If i can restore my mbr back to the way it was without vista knowing i can figure out the rest.

p.s. i have been doing my bit to help other noobs if this will sway you in any way :)

---

### Post by Sparkster185 on 2007-05-29
I think you can just resize your existing NTFS partition to take up the remainder of the disk, this should erase your linux partition and remove Ubuntu.  I'm not sure how to edit grub tables though.

---

### Post by Delkster on 2007-05-29
> **flip_flop said:**
> I wanted to try a few distros before committing to one however cant uninstall ubuntu or at least grub.
You probably don't need to uninstall Ubuntu if you want to replace it with a different Linux distribution. The installation routines of most distros will allow you to choose which partition you want to install the new distro on. If you tell it to install on the partition where Ubuntu is, it will probably just wipe the partition and install the new distro in Ubuntu's place. The same goes for grub.

---

### Post by flip_flop on 2007-05-29
Thanks - do you know of anyway to restore the mbr if i need to.  Would like the option of going back if i want.

If i could find the source to grub and the installation scripts i am willing to see what i can do to prevent other noobs being in same situation - i know some members really hate the idea of an uninstall but it might help someone.

---

### Post by ajgreeny on 2007-05-29
Restoring the mbr depends upon the type of windowsXP Cd you have.  If it is a full oem xp disk, rather than a reinstall software CD, you just start up with the windows XP CD in the drive.  You then go to the recovery console and use the command fixmbr.  This should get you back to where you were before you installed linux.

If you have a restore software CD from your manufacturer, however, you may not be able to do this and will need to use some other system which I can't help you with I'm afraid.

Good luck!

---

