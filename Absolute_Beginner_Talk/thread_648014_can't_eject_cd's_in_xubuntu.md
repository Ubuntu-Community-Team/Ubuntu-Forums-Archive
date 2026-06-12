---
title: "can't eject cd's in xubuntu"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by rolypolycat on 2007-12-23
Hello!

I'm running Xubuntu Feisty Fawn. I can load a cd or dvd, but I can't eject it without right-clicking and hitting eject. When I hit the eject button, I get this message:
/org/freedesktop/HAL/devices/storage_model_DVDRW_LH_16W1P- given device is not a volume or drive.
Seeing as how it most certainly is a drive, and it's right there, I don't understand why it doesn't eject automatically. Every other linux distro I tried has no problem with this. Or is this another bug in Xubuntu, like the one with the terminating terminal?
Any ideas how I can eject my cd's just by pushing the button? It also confuses other users on my machine, too.
Any help is greatly appreciated. Thanks!!

sincerely,
rolypolycat

---

### Post by blueridgedog on 2007-12-23
A similar issue was discussed here:

[http://www.linuxquestions.org/questions/linux-software-2/gnome-volume-manager-auto-mount-issue-606676/](http://www.linuxquestions.org/questions/linux-software-2/gnome-volume-manager-auto-mount-issue-606676/)

In this case Gnome volume manager was not starting on boot.

---

### Post by rolypolycat on 2007-12-23
Hello!
Thanks for the tip. It sounds just like my problem. The post didn't tell how to add the gnome volume manager to start on bootup, though. How do I do this? I want to try this fix out for myself, but I'm not sure where to start. Thanks!

sincerely,
rolypolycat

---

### Post by rolypolycat on 2007-12-24
Hello!

Well, I decided to try hunting down the solution again online, and found a tip on the Gentoo forums. I used Add/Remove programs, found gnome volume manager wasn't installed, and installed it. I logged out, then logged in again. Now here's the weird part: When I eject a cd, it will now eject, but I still get the same error message! According to XFCE's  Autostarted Applications menu, GVM is there and ready to start, so why the error message?
At least it's not so annoying as not ejecting the cd at all, but I want to know why it says this, and how to fix it. Especially if it might come back to pester me again in another problem.
Thanks in advance!

---

### Post by blueridgedog on 2007-12-24
Ok, let's see if it is running.  Run the following few command and post the results:

 ps ax | grep gnome-volume

If it is not running, you can start it with:

sudo gnome-volume-manager &

To configure gnome-volume-properties or use System > Preferences > Removable Drives and Media, perhaps there is a clue there.

Finally for additional "debugging"  You can get a terminal window up and type:

sudo tail -f /var/log/messages

Leave this running then insert a cd and eject it after about 30 seconds.  You can post anything interesting.

I think GVM is failing at some point, but I would like to try a new disk.

---

### Post by rolypolycat on 2007-12-25
Hello!
Now for an update. I logged out, logged back in to fix something I forgot, logged out again, then left the computer for about 12 hours or so. I came home, and played 2 music cds. Both ejected okay, and there was no error message this time. Maybe I just needed to log out twice to get GVM to run right? Anyway, it seems to be playing nice now. I thank you for your help, and hopefully, the problem has solved itself. If it does anything funny again, I'll try your suggestion. Thanks again!

sincerely,
rolypolycat

---

### Post by blueridgedog on 2007-12-25
Merry Christmas.

---

