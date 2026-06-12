---
title: "Complete Redesign of my layout - Need Help"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by codeblue315 on 2007-07-29
Ok, I am currently running Kubuntu on a 250gb hard drive. I also have a 500gb hard drive used for storage. What I am trying to do is reinstall Kubuntu on the 500gb hard drive and use that as my main OS (of course) and then install Windows XP on my 250gb hard drive. What I plan on doing is booting up the Live CD and using gparted to delete all of the partitions I have to basically start from scratch. What I am wondering is, when I do all this, how is GRUB going to react? Am I going to have to use the fixmbr on the XP disc or will GRUB just no longer exist?

---

### Post by IamAcoconut on 2007-07-29
Don't know how GRUB will behave if it's on MBR :|

Just a thought though - why do you need so much space for Windows? If you used FAT on the data storage partition it could be accessed by both systems.

---

### Post by 505 on 2007-07-29
Well, if you're wiping out everything you can just start from scratch. Grub will also be reinstalled. Some advice though, if you want to run Windows and Ubuntu, is is far easier to install windows first, than Ubuntu. Grub will install and detect both. Just keep the 250GB drive as master, and the other as slave. Windows doesn't play nice if it is not on the first drive. If you want to do it the other way, you can, but you need an extra Grub boot options to remap the drives.

---

### Post by p_quarles on 2007-07-29
> If you used FAT on the data storage partition it could be accessed by both systems.
That is true, but FAT32 will fragment considerably faster than ext3 (which experiences very, very little), so it ultimately makes more work. 

@codeblue: When you say you want to start from scratch, do you mean you'll be installing both OSes from scratch? If so, you should get good results by simply installing XP first, and then letting GRUB modify the MBR. But, I've never tried to do this on a two-disk setup, so I there may be more involved.

---

### Post by codeblue315 on 2007-07-29
Well, it's not really a storage issue, it's more of an organizational issue. I also have a 250gb external hard drive that I use for storing all of my files and whatnot, and it's in FAT32.

I just don't want GRUB screwing everything up when I'm done doing all of this.

Ok, so install XP first, then Ubuntu, and everything should be fine. Awesome, thanks everyone!

---

### Post by Nevis on 2007-07-29
Since you're reinstalling both OSes (If I read you correctly) then why not just install Windows on the 250 GB disk then do the Ubuntu install and let it configure GRUB?

Also, if you use ntfs-3g you won't have to use FAT32. Better yet, get ext2IFS for Windows and you can use the better ext2 file system for common storage!

---

### Post by Nevis on 2007-07-29
Also, here's a guide for dual boot on multiple drives :-)

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by p_quarles on 2007-07-29
> **codeblue315 said:**
> Well, it's not really a storage issue, it's more of an organizational issue. I also have a 250gb external hard drive that I use for storing all of my files and whatnot, and it's in FAT32.

I just don't want GRUB screwing everything up when I'm done doing all of this.

Ok, so install XP first, then Ubuntu, and everything should be fine. Awesome, thanks everyone!
Are you saying you don't want to use GRUB as your boot menu? If not, you can obviously use the BIOS to select which drive to boot from. If that's what you're trying to do, I'd consider just disconnecting the Windows drive while installing Ubuntu.

---

