---
title: "Xp onto Ubu"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Ivantheterrible on 2007-10-01
Hey everyone I just installed Ubuntu last week but accidentally formated the harddrive (I had XP) and now I only have Ubu...My question to all of you is ...Can I put XP on a partition onto Ubuntu?...Remember.. I am installing XP onto Ubu not the other way around....Will this be hard to do? and are there any guides to help me?...any input would be helpful

-Ivan

---

### Post by Pumalite on 2007-10-01
Is always best to install XP first (likes to be sda1). If they are both fresh installs, I would reformat the drive ntfs, install XP, then resize the XP partition with Gparted and then install Ubuntu again, installing Grub to the MBR.

---

### Post by Ivantheterrible on 2007-10-01
I am sorry but I have no clue what you mean...Unless you mean...deleting Ubuntu..putting windows in first and then reinstalling ubuntu...but otherwise...not so much

-Ivan

---

### Post by teet on 2007-10-01
> **Pumalite said:**
> Is always best to install XP first (likes to be sda1). If they are both fresh installs, I would reformat the drive ntfs, install XP, then resize the XP partition with Gparted and then install Ubuntu again, installing Grub to the MBR.

If you haven't done much to your ubuntu install, I would suggest reformatting and starting over clean.  However, I wouldn't reformat the whole hard drive as NTFS.  From the windows installer, reformat the drive, and make your windows partition as big as you need it to be.  Then after you get windows installed, install ubuntu on the remaining free space.  No sense in resizing a freshly made partition!

However, if you've done a lot of stuff to your ubuntu install and don't want to lose it, you CAN go ahead and resize your ubuntu partition and install windows in the free space.  Windows will overwrite the master boot record so you'll lose GRUB (i.e. you won't be able to boot into ubuntu).  Then you'll need to grab an ubuntu live cd and reinstall grub to the MBR from that.  It's not too hard if you know what you're doing.

-teet

---

### Post by alienexplorers on 2007-10-01
As Pumalite mentioned you should install XP first to your drive, leaving room for Ubuntu.  Then install Ubuntu and use the freespace you left available to make your partitions for Ubuntu.  Install grub on the MBR and you are set to go.

---

### Post by Pumalite on 2007-10-01
That's what i said, under the impression that they were both new installations.
Here is Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
You can also resize Ubuntu's partition, format ntfs and install XP in sda2, XP would overwrite MBR and you would have to re-install Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Your choice.

---

