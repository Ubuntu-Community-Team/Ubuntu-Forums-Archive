---
title: "partition hd AFTER installation"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by rkrug on 2007-04-02
Ok, i'm going to partition my hard drive with half ubuntu and half windows.

I already have ubuntu installed on my hard drive. 

Can somebody walk me through how to do this?

---

### Post by jem7v on 2007-04-02
To partition your drive and make space for Windows, I'd probably use the GParted LiveCD, myself.
GParted LiveCD site: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) talks about using GParted to create a new /home partition on your hard drive, which is similar to what you'd be doing (i.e., creating a new partition for Windows.)  It might also be smart to create a separate /home partition while you're at it, as the benefits are manyfold!


As for installing Windows AND Ubuntu? Usually you have to install Windows first and then Ubuntu. Here's why:
- Ubuntu will set up a dual boot system when being installed.
- Windows will horde the Master Boot Record (MBR) for itself and not tell the computer there are other ways it could boot up. (Hooray for Microsoft!)
With a bit of effort you can *probably* get it to recognise both again by restoring GRUB: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by rkrug on 2007-04-03
if i were to put in the windows install cd would it ask me which partition to install on?

---

