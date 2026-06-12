---
title: "How To Uninstall When Using a Dual Boot"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Hawkeye05 on 2007-08-29
I'm Using feisty with a dual boot with XP and I am taking a Linux Administration class that i found out uses Fedora, I love Ubuntu but I'd really prefer to use what the class is using, is there a way that i can just swap out Ubuntu for Fedora?  Or how do i basically go about uninstalling Ubuntu while installing Fedora while leaving my XP Partition intact and the bootloader still working?

Thanks In Advance

---

### Post by ts51 on 2007-08-29
Why not just make more partitions, then use Ubuntu's GRUB bootloader to boot XP, Ubuntu, and Fedora? Or, use VirtualBox in Ubuntu or XP to use Fedora.

---

### Post by forestpixie on 2007-08-29
I would assume that if Ubuntu is on a partition you could just install over the top of Ubuntu - but there's nothing to stop you triple booting if you have the room.

---

### Post by kellemes on 2007-08-29
The fedora installer will let you install Fedora on the partitions where Ubuntu is now, just let the installer format the partitions.
You don't need to uninstall anything.

---

### Post by LaRoza on 2007-08-29
> **ts51 said:**
> Why not just make more partitions, then use Ubuntu's GRUB bootloader to boot XP, Ubuntu, and Fedora? Or, use VirtualBox in Ubuntu or XP to use Fedora.

The easiest thing to do, a triple boot.

I would:
* Defrag Windows
* Back up all data
* Delete Ubuntu partition
* Create 2 partitions, one for Fedora, one for Ubuntu
* You now have 4 partitions, NTFS, EXT3, EXT3, Swap
* Install Fedora, install Ubuntu

This isn't the best way, but it will work the easiest.

You can do it without deleting Ubuntu, but the above method will get all bootable.

---

### Post by Hawkeye05 on 2007-08-29
Yeah, i dont have the storage to do a triple boot.  But if i install Fedora over Ubuntu will the bootloader still work?

and i dont have the Ram or processing heft to use a virtual machine

---

### Post by ts51 on 2007-08-29
Just do this: [http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm) 
That should remove the GRUB bootloader. Then go into windows and format the Ubuntu partition. There we are, Windows only. Boot from the Fedora CD and install on Ubuntu's old partition. It might and should work. But I don't know if it will work. Someone should probably verify this before you listen to me.

---

### Post by Duck2006 on 2007-08-29
You can do it all from the fedora cd. Just let the fedora install over write the ubuntu install, and it will reinstall grub so you will be able to boot the system as a dual boot system

---

### Post by ts51 on 2007-08-30
OK... I will confirm it. Put the fedora cd in your computer. Boot it. Install it, but when it asks you where select Ubuntu's partition. It will install. And, if everyone hear is write, it will make a dual boot with XP and Fedora completely killing Ubuntu. I think it will work, and if I was in your shoes I would do it that way. But I could be wrong, so do it at your own risk.

---

### Post by ts51 on 2007-08-30
If that works, let us know and also, mark the thread as [solved], {solved}, [fixed], etc;

---

### Post by dpar on 2007-08-30
I agree with everyone else......just install fedora to the ubuntu partition......it will install it's own bootloader.

---

