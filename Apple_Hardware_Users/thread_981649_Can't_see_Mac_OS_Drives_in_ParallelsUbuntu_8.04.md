---
title: "Can't see Mac OS Drives in Parallels/Ubuntu 8.04"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by burobaaje on 2008-11-13
I have installed ubuntu 8.04 in Parallels 4.0.  It runs very well.  But, after installing Parallels Tools and having it configured to show my Mac OS HD, it still does not show up in ubuntu.  Anyone have any ideas?  BTW all other functions of Parallels Tools seem to work fine.

This works fine with XP but could it be that I have to go to the fstab and edit it even though Parallels Tools is usually all that is needed to see the Host drives.

Thanks!

---

### Post by mfox on 2008-11-14
Did it work in Parallels 3?  I have heard that there are some bugs in Parallels 4, and the company hasn't been very good about the implementation of features on Linux VMs that work in Windows VMs.

Have you implemented sharing on the Mac side?  If I recall correctly, shared drives would appear under /mnt in Ubuntu running on Parallels.

---

### Post by burobaaje on 2008-11-14
"did it work in 3.0?"

Sorry, I  never tried using 3.0.

I have sharing on every way possible and other computers on the network can see each other.  I'll check out the /mnt.

---

### Post by mfox on 2008-11-14
I may have mislead you.  Shared folders in Linux wasn't even possible in Parallels 3; they just brought it in in Parallels 4 (which I'm not using).  In Parallels 3 in a Windows VM, a shared folder shows up on the desktop.  I would expect something similar in Parallels 4 with a Linux VM, although you may be required to manually mount the shared folder with a "mount -t hfsplus" type of commnand.

---

### Post by burobaaje on 2008-11-14
I stumbled on the solution.  First you must install Parallels Tools in ubuntu.  I don't think you could install tools in Parallels 3.  And Tools adds the same functionality as it does to Windows.  The mouse will change from ubuntu to Mac OS without having to unlock it from the keyboard.  Much better than v3.

Tools installs a couple of lines in fstab as listed below.  You change none to your Mac's drive designation, in my case disk0s3 and that drive shows up on the desktop when you reboot ubuntu as psf.


#Parallels Shared Folder mount
none          /media/psf   prl_fs   defaults,share     0       0

#Parallels Shared Folder mount
/dev/disk0s3          /media/psf   prl_fs   defaults,share     0       0

Installing Tools is a bit hard to understand from the directions given by Parallels.  When you select the pull down menu item to "Install Parallels Tools", it mounts a CDROM on the desktop.  You then have to go into Terminal, access the CDROM and give the command ./install.  Tools will then install.

Hope this helps somebody else!

---

### Post by steronius on 2009-06-09
It seems that after certain ubuntu updates, VM tools need reinstalling. (This happens to me in both VirtualBox and Parallels.)

Your above solution of editing fstab did not work for me.

However, reinstalling Parallels tools did.

To re-install tools, do the following:
1) While running the ubuntu VM, use the Parallels Tools menu in OSX and choose Vurtual_Machine-->Install_Parallels_Tools (it will likely NOT auto-run, so do the following: )
2) In ubuntu, in a terminal, run "cd /media/cdrom ; sudo ./install" and follow the dialogs.

---

### Post by cyberdork33 on 2009-06-10
> **steronius said:**
> It seems that after certain ubuntu updates, VM tools need reinstalling. (This happens to me in both VirtualBox and Parallels.)

this is because certain drivers are built against the currently running kernel. If the kernel is updated, those drivers do not work.

---

