---
title: "3 questions I've been meaning to ask (various problems)"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-11-29
1.  I have 2 hard drives.  On the first hard drive is a partition for XP and Ubuntu.  The second hard drive is data only.  XP sees the second hard drive fine ALL the time, but I often have problems when I boot into Ubuntu after restarting XP and my second hard drive does not appear. (i.e. not mounted).  I have no idea why this happens and sometimes I have to restart the computer 5-6 times before I can finally access my second hard drive.  Any ideas?  

2.  I can't log off Ubuntu successfully.  It crashes every time I go to System > Quit, the screen freezes and I have to restart manually.  It's been this way since I upgraded from 7.04.

3.  Is there any way to make programs that start up through 'Sessions' start up minimized? Every time I boot Ubuntu, I have certain programs such as Thunderbird and KTorrent start up automatically, but is there any way they can start minimized instead of clutter up the desktop?  I would prefer this.

Thanks :)

---

### Post by kelbizzle on 2007-11-29
Ehhh for your hard drive issue. The cause may be your jumper pins on the HDD make sure that the primary and slave pins are in the correct places on both drives. One needs to be setup as a primary and the other needs to be setup at a slave.  'have the same issue but am too lazy to fix it. Instead I just quickly open a terminal....
```


$ sudo nano /etc/fstab 
 
```

When using nano CTRL+O to save it CTRL+X to exit


```
/dev/sdb1 /media/xxtra reiserfs defaults 0 0
```

I have to change mine from /dev/sdb1 or /dev/sdc1 when ever I realize the mount isn't up there. To find out what yours is you can type  fdisk -l to find out. 

Then you have to type...
```
sudo mount -a

```

To remount stab

---

### Post by alwiap on 2007-11-29
great thanks!  that helped for the 1st question.

does anyone have any ideas about my other 2 problems?

---

### Post by quandary on 2007-11-29
> **alwiap said:**
> great thanks!  that helped for the 1st question.

does anyone have any ideas about my other 2 problems?

I don't know what causes your logoff problem, it works well for me.
But instead of logging of, you can use CTRL + ALT + BACKSPACE as workaround.
This quits your programs, restarts the x-session and shows you the login screen. Has the same effect as logoff, but is faster and probably doesn't crash.

For your third problem: I don't get any programs started up at system-start.
So you probably have them in some config file/batch script.

Find out the file's name, and add a command line option like Thunderbird-minimized (consult the man pages for the actual command option)

You can use grep "thunderbird" /etc/* 
or grep "thunderbird" ~/*
to search for the batch script calling thunderbird.

---

### Post by philinux on 2007-11-29
Install startup manager it seems to sort out shutdown as well. My shutdown time is now 13 seconds.

---

### Post by alwiap on 2007-11-29
> **quandary said:**
> I don't know what causes your logoff problem, it works well for me.
But instead of logging of, you can use CTRL + ALT + BACKSPACE as workaround.
This quits your programs, restarts the x-session and shows you the login screen. Has the same effect as logoff, but is faster and probably doesn't crash.

For your third problem: I don't get any programs started up at system-start.
So you probably have them in some config file/batch script.

Find out the file's name, and add a command line option like Thunderbird-minimized (consult the man pages for the actual command option)

You can use grep "thunderbird" /etc/* 
or grep "thunderbird" ~/*
to search for the batch script calling thunderbird.

Thanks for the Restarting X idea, i knew how to do that but never thought of that to log off.  I'll just do that from now on.

I read the manual of thunderbird and ktorrent but there aren't any options to start it minimized, I'll try the other ideas later.  again thanks.

and philinux, I've had startup-manager installed since I upgraded, I still have the problem. :confused:

---

### Post by philinux on 2007-11-29
Sounds like a power management problem then.

What're your system specs?

---

### Post by philinux on 2007-11-29
Have a click on the gutsy known bugs in my sig as well.

---

### Post by quandary on 2007-11-29
> **alwiap said:**
> Thanks for the Restarting X idea, i knew how to do that but never thought of that to log off.  I'll just do that from now on.
Most times, it's even faster than logoff   ;-) ;-) ;-)

> 
I read the manual of thunderbird and ktorrent but there aren't any options to start it minimized, I'll try the other ideas later.  again thanks.

You could delete thunderbird from startup and instead install a notification utility:
apt-get install mail-notification

I just couldn't believe you can't start them minimized, and googled a bit around, but you are right. But I found a solution:
[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)
With AllTray you can dock any application with no native tray icon (like Evolution, Thunderbird, Terminals) into the system tray. A high-light feature is that a click on the "close" button will minimize back to system tray.  It works well with Gnome,  KDE,  XFCE 4*, Fluxbox* and WindowMaker*

---

