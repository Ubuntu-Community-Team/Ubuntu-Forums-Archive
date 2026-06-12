---
title: "Trying to install Ubuntu"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by munchkinesque on 2008-03-13
I'm trying to install Ubuntu 6.06 onto my PC from a CD.  I put the CD in the computer when it starts up, I select option 1 (install), and it seems like it installs the OS.  I have the desktop, Firefox, etc.  However, it still runs everything off of the CD (it accesses the CD for everything), and when I tell it to shut down, it uninstalls everything.  The next time I turn the computer on (without the CD in), Windows starts up again.  How do I erase Windows (2000 pro), and how do I make Ubuntu my permanent OS so I don't need the CD?

Many thanks!

---

### Post by coolbrook on 2008-03-13
My assumption is that you chose to *Start or Install Ubuntu* and that you didn't choose to Install when the Live CD's (RAM) version of the desktop loaded.  Try to install again.  After choosing to Start or Install Ubuntu, you should have a choice to click on a desktop icon to install.  During the installation, choose to use the entire disk for your installation.  That should wipe your Windows installation.

---

### Post by Duck2006 on 2008-03-13
Did you click on the install icon on the desktop?

---

### Post by Tatty on 2008-03-13
You have not actually installed Ubuntu yet... When you but the desktop CD in and boot, it simply runs the CD directly from the CD drive.  This can be very useful if you ever need to rescue a broken system, or if you simply want to test out Ubuntu on your hardware.

To install:

1. Boot into ubuntu with the CD
2. Click on the "install" icon on the desktop
3. Go through the install wizard
4. When you reboot, make sure you take the CD out of the  drive (otherwise you will boot from CD again)
5. If all went well, you should now boot up into ubuntu from your hard disk.


Warning: I assume you dont want to lose Windows off your computer... make sure you partition your hard drive correctly.  This guide should help you [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
Vista Warning:If you have Vista make sure you partition it with its own partition utility - vista installs dont play nicely with the ubuntu partition manager (gparted).  Just shrink your Vista partition and leave the free space for ubuntu to use.

---

