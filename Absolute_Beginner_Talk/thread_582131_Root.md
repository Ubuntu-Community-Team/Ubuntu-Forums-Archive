---
title: "Root"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by prob69 on 2007-10-19
I have just installed the latest Ubuntu 7.10 as a new user. All works very well but wanted to delete some icons off of the desktop but it told me I had to be ROOT user. I hunted about and managed to change the password for the root user but when I log on from the logon screen, it tells me that I could not log on as root from here.
Do I take it that ROOT has administrator capabilities and my user name does not?
How do I log on as ROOT so I can delete items from desktop?
Thanx

---

### Post by Linux_Man on 2007-10-19
What icons on the desktop were they? You shouldn't need to be root to delete items on your desktop (Your deskop should be in your home directory so you should have Read/Write acess to it, did you make a home partition and set it up correctly? Or did you chose the default options?

---

### Post by Arthur Archnix on 2007-10-19
Well, depending upon what the icons are there are a number of ways to do this, none of which require logging in as root, although if that is your goal you need to look at >System >Administration >Login Window, where under the security tab you'll find a check box allowing local administrator to login.

This is not recommended however. So, maybe tell us what icons are on the desktop that you don't want there anymore, and that right-clicking and choosing delete doesn't work for.

Some icons will be found by looking in ~/home/Desktop
```
cd ~/Desktop
ls
```
Let's say this shows us "stubborn.file"
```
sudo rm stubborn.file
```

Other icons might be on your desktop but not in your folder, things like internal partitions, maybe hotplugged usb devices, maybe a trash can. You can get rid of these by doing:
```
gconf-editor
```
and browsing to >apps >nautilus >desktop, and unchecking the things you don't want showing up.

---

### Post by prob69 on 2007-10-19
The icons that are showing are Hard Drives. Within my computer I have 2 hard drives. The first drive contains my Vista partition that I have called "SYSTEM", then another partition that Ubuntu is installed in and then another partition that I have called "HDRIVE2"
The Second drive has no partitions and I have called that "DATA"
The 3 Icons that are showing on the desktop are DATA,HDRIVE2 and SYSTEM. I may have been doing something wrong here but I right clicked on an icon and went unmount volume but it said I do not have the priviledge. I guessed I would have to be logged in as root to delete them. I only installed tonight so still very new to this.
Am I trying to delete them of the desktop the correct way?

---

### Post by Arthur Archnix on 2007-10-19
No, use the gconf-editor as mentioned above. Type that into a console and uncheck show mounted volumes...or something ;)

---

### Post by bapoumba on 2007-10-19
You have two solutions. Anything mounted in /media will show up on the desktop.
So either you go to gconf-editor as mentioned, but then any hot plugged device will not show up on the desktop, or you mount  your partitions elsewhere.

What is the output to:
```
cat /etc/fstab
```

---

### Post by prob69 on 2007-10-19
Thats done the trick. Cheers.

---

### Post by Arthur Archnix on 2007-10-19
Ah yes... may have forgotten to remember to mention that. #-o

---

