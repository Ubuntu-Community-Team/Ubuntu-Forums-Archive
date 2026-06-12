---
title: "Trying to figure what happened (Help please)"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-03-10
My son was playing with my newly installed Kubuntu Gutsy KDE4 machine.  He says he remembers something about a Daemon statement and then the machine rebooted.  

Since it came back up, we only have Terminal mode.  No graphical interface.

I can see an initial Kubuntu splash screen.  But from the logon prompt on-ward, its only terminal mode.

Can anyone offer info on the daemon he might have stopped, and how to recover XWindows?

Bill

---

### Post by handydan918 on 2008-03-10
No idea about the daemon, but if you do ```
sudo dpkg-reconfigure xserver-xorg
```
you will get a text based series of menus to reset the xserver settings. If unsure, use the defaults and post back with any problems.

---

### Post by bmachia on 2008-03-10
Well,
I tried to do your suggested command:  sudo dpkg-reconfigure xserver-xorg
The computer responded with xserver-xorg Broken or Not Completely Installed.

So, my next step was:  sudo apt-get install xserver-xorg
The Computer then install xserver-xorg without any errors.  Again, I went back to your suggestion:  sudo dpkg-reconfigure xserver-xorg, and the ASCII menu system took me through quite a number of questions from Mouse, to Monitor.  It told me it was writing a configuration file.  I thought I was good to go....
But, (as Gilder Radner said) "its always something".  Generally stuff that I don't fully understand.

I still have no graphics and I'm in terminal (konsole) mode.  It looks like its going into a graphical display right up to the Login prompt.

However, this time I saw the error:  kinit: No resume image, doing normal boot...

Any thoughts?
I'm really hoping I can dig myself out of this one.

Bill

---

### Post by handydan918 on 2008-03-10
Well, if nothing else, you could boot the live cd and copy/paste the /etc/X11/xorg.conf file from the cd onto the harddrive...
I can't recall if Ubu has a xwindows reinstallation utility or not. 
Mepis does....darned handy, too.

---

