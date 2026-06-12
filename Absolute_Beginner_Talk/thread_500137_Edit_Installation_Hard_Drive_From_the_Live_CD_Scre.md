---
title: "Edit Installation Hard Drive From the Live CD Screen?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by jimcrockett on 2007-07-13
I need to get to my second HD that has the Ubuntu installation to change my monitor settings to avoid "Signal Out Of Range".  In the live CD, I mounted the installation HD (sudo mount /dev/hdb1 /mnt) and viewed the /x11/xorg.conf file and see the wrong refresh rates, which I want to change.  This is one problem that is preventing Ubuntu booting from the HD installation.

In the live CD, I can mount the installation HD.  Now, how do I get into that drive and modify the Monitor Section?

---

### Post by sad_iq on 2007-07-13
Won't commenting out (put a # in front) the **HorizSync **and** VertRefresh** do the job?? Or google the horyzontal and vertical values from your monitor and replace the ones that are in xorg.conf. Also you don't need the Livecd to modify xorg.conf...just boot your normal installation...and when the error appears press ALT+Ctrl+F1 , login, type ```
sudo /etc/init.d/gdm stop
```then ```
sudo nano /etc/X11/xorg.conf
``` and modify the file to your needs!!!

---

### Post by jimcrockett on 2007-07-13
My problem is that the normal installation crashes, and I can't get to the command line when it does from there when it does.  I figure if I can get to it from the live CD, I can modify the Monitor section with the correct values for my monitor.

Or, maybe there's another way to get to the files in my installation so I can change it?

---

### Post by sad_iq on 2007-07-13
Well then...after you mount the hdd do a simple cd /mnt and sudo nano /mnt/etc/X11/xorg.conf and modify it...should work...I Think!!!
 Or when grub starts press esc and choose recovery mode...that will take you to a command prompt...and work from there!!!

---

### Post by jimcrockett on 2007-07-13
Thanks - I got into the terminal and after much working around, I managed to get the monitor resolution right in the x drive.  Booted on the live CD and x-drive - still have the problem, so something else is happening.  Also crashes on startup on the x-drive, so I quit for now.  I am on dial-up so I'll have to go get another live CD download from a DSL connection.  Even though the check disk in live CD seems to work OK, I think the disk may be corrupted.

Thanks again - now I know how to edit the x-drive in live CD.

---

