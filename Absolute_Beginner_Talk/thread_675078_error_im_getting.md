---
title: "error im getting"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by bamman93 on 2008-01-22
imgetting an errer that says
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

how do i mannuly run this and fix the erroer thanks

---

### Post by divague on 2008-01-22
open a terminal and type

sudo dpkg --configure -a

---

### Post by Shazaam on 2008-01-22
Go to "Applications>Accessories>Terminal. When it opens you will see something like this with a blinking cursor-- yourusername@yourusername-desktop
Type in...
```
sudo dpkg --configure -a
```
hit enter and you will be prompted for your password. This will be the password you log into Ubuntu with. The blinking cursor will not move, don't worry it will be entered ok. Hit enter, after about a seconds delay the prompt will come back (unless there are errors). You should be fine after that.
What this code does is configure any unconfigured packages.

---

### Post by bamman93 on 2008-01-22
ok so i did that now its telliong me i have a broken package how do i fix that

---

### Post by Shazaam on 2008-01-22
Try this next in terminal.....
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bamman93 on 2008-01-22
now it says 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

also i downloaded a mac emulater how do i use it 
sorry im new to linix

---

### Post by rosegarden78 on 2008-01-22
May I suggest you consider using Synaptic or a package management program with a GUI?  Usually reconfigure -a does the trick for me.  This could happen if you're using a 3rd-party Debian package.  Long-established programs from the repositories don't usually do this.  Good luck!  By the way did you say Mac emulator?  The WINE project works great for Windows legacy apps.  I think the Bochs or Mac Emulators require files from the original computer just like WINE needs the Common Files from XP to use many advanced programs.

---

### Post by Shazaam on 2008-01-22
> **bamman93 said:**
> now it says 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

AFAIK the error you are getting now usually means either the auto-updater or Synaptic was running when you tried the last 2 commands. Turn them off if they are running and try again.

---

