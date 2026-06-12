---
title: "Help, locks up on startup."
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by mikeescott on 2007-02-14
I installed automatix from here 

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_386.29)

and I installed envy to get started on my ati drivers. then I went through the xorg menues. Now it locks up on startup at the Ubuntu screen. I was watching automatix as it installed and it was removing a lot of files. Is that normal? Can I do anything in recovery mode to fix this? alt+F1 did nothing.

---

### Post by ukripper on 2007-02-14
> **mikeescott said:**
> I installed automatix from here 

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_386.29)

and I installed envy to get started on my ati drivers. then I went through the xorg menues. Now it locks up on startup at the Ubuntu screen. I was watching automatix as it installed and it was removing a lot of files. Is that normal? Can I do anything in recovery mode to fix this? alt+F1 did nothing.

try failsafe session first, when gdm starts put your username and password enter failsafe gnome session and change settings within gnome.
 
if that doesn't work try in console mode 

run sudo dpkg-reconfigure xserver-xorg 

or find backup for xorg and replace the xorg.conf with that.


Need more info though

---

### Post by mikeescott on 2007-02-14
> **ukripper said:**
> try failsafe session first, when gdm starts put your username and password enter failsafe gnome session and change settings within gnome.
 
if that doesn't work try in console mode 

run sudo dpkg-reconfigure xserver-xorg 

or find backup for xorg and replace the xorg.conf with that.


Need more info though

How do I start a failsafe session?
What is gdm?
Where do I find a backup of sorg?

---

### Post by ukripper on 2007-02-14
> **mikeescott said:**
> How do I start a failsafe session?
What is gdm?
Where do I find a backup of sorg?

when login screen pops up there is option to select session -GNOME, Default, Console Login, Failsafe.

Click on failsafe, put your login and password. you should be able to log into failsafe mode.

---

### Post by mikeescott on 2007-02-14
> **ukripper said:**
> when login screen pops up there is option to select session -GNOME, Default, Console Login, Failsafe.

Click on failsafe, put your login and password. you should be able to log into failsafe mode.



can't get that far. I select the kernal and it locks just after that. If I could get ther, I have automatic login enabled. All I can get to now is restore prompt. root@mike

---

### Post by ukripper on 2007-02-14
> **mikeescott said:**
> can't get that far. I select the kernal and it locks just after that. If I could get ther, I have automatic login enabled. All I can get to now is restore prompt. root@mike


type at that prompt:
$ startx 

paste output here if it gives errors

---

### Post by mikeescott on 2007-02-14
> **ukripper said:**
> type at that prompt:
$ startx 

paste output here if it gives errors

Here is everything on my screen after entering startx:


```
X: warning; process set to priority -1 instead of priority 0

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux mike 2.6.17-11-generic #2 SMP Thu Feb 19:52:28
 UTC 2007 i686
Build Date: 07 July 2006
           Before reporting problems, check http://wiki.x.org
           to make sure that you have the latest version.
Module loader present
Markers: (--) probed, (**) from config file, (==) default setting,
            (++) from command line, (!!) notice, (II) informational,
            (WW) warning, (EE) error, (NI) not important, (??) unknown.
(==) Log file: "/var/log/Xorg.conf"
(==) Using confid file: "/etc/X11/xorg.conf"
(EE) No devices detected

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaining.
root@mike:~#
```

---

### Post by mikeescott on 2007-02-14
> **mikeescott said:**
> Here is everything on my screen after entering startx:

Is there a way to fix the xorg file from here or is there a way to fix it from Windoze?

Is there a way to access files on the Linux hard drive from windoze?

---

### Post by mikeescott on 2007-02-14
> **mikeescott said:**
> Is there a way to fix the xorg file from here or is there a way to fix it from Windoze?

Is there a way to access files on the Linux hard drive from windoze?

OK, I can get into Ubuntu from the live cd. Can I copy the xorg file from there to the installed Ubuntu? How would I do that? Please help.Thanks, Mike

---

### Post by ukripper on 2007-02-15
> **mikeescott said:**
> OK, I can get into Ubuntu from the live cd. Can I copy the xorg file from there to the installed Ubuntu? How would I do that? Please help.Thanks, Mike

First of all, go back to recovery console, on prompt type following to reconfigure your xorg:

$ sudo dpkg-reconfigure xserver-xorg


The above command will take you to configuration of xorg. 

Only, if that doesn't work then try the following:

list contents in X11 through command line:
$ ls /etc/X11

Find the backup for xorg.conf(if there is any), i am assuming backup name is xorg.conf.backup

$ sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

backup will replace yopur current xorg.conf

---

### Post by mikeescott on 2007-02-15
> **ukripper said:**
> First of all, go back to recovery console, on prompt type following to reconfigure your xorg:

$ sudo dpkg-reconfigure xserver-xorg


The above command will take you to configuration of xorg. 

Only, if that doesn't work then try the following:

list contents in X11 through command line:
$ ls /etc/X11

Find the backup for xorg.conf(if there is any), i am assuming backup name is xorg.conf.backup

$ sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

backup will replace yopur current xorg.conf

I will try that tonight when I get home. Last night I loaded the live cd and copied the xorg.conf file from there to an external drive. Then I went into Windoze and found a program that lets me read/wright to the Linux drive. I then replaced the xorg.conf file from the external drive to the Linux drive. I restarted and it made it past where it locked up before, but it would not go past the tan/orange screen where the programs load. It was just a blank screen though, no programs were loading (ie. gnome, nautalis, etc)

---

### Post by ukripper on 2007-02-15
> **mikeescott said:**
> I will try that tonight when I get home. Last night I loaded the live cd and copied the xorg.conf file from there to an external drive. Then I went into Windoze and found a program that lets me read/wright to the Linux drive. I then replaced the xorg.conf file from the external drive to the Linux drive. I restarted and it made it past where it locked up before, but it would not go past the tan/orange screen where the programs load. It was just a blank screen though, no programs were loading (ie. gnome, nautalis, etc)

Try reconfigure first and let me know if you still have problems. 


Once xorg is configured GDM and Nautilus should work. It will also allow you to change session at login screen such as failsafe and gnome sessions. try it with failsafe if you can't go past gnome session:guitar:

---

### Post by mikeescott on 2007-02-15
> **ukripper said:**
> Try reconfigure first and let me know if you still have problems. 


Once xorg is configured GDM and Nautilus should work. It will also allow you to change session at login screen such as failsafe and gnome sessions. try it with failsafe if you can't go past gnome session:guitar:


I tried to reconfigure and this is what I got:

```

Package 'xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
Use dpkg --cuntents (= dpkg-deb --contents) to list their contents
/usr/sbin/dpkg-reconfigure: xserver-org is not installed
```

---

### Post by ukripper on 2007-02-16
> **mikeescott said:**
> I tried to reconfigure and this is what I got:

```

Package 'xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
Use dpkg --cuntents (= dpkg-deb --contents) to list their contents
/usr/sbin/dpkg-reconfigure: xserver-org is not installed
```



Are you putting xserver-xorg or xserver-org?

Make sure command should be as below exactly:

**$ sudo dpkg-reconfigure xserver-xorg**

---

### Post by mikeescott on 2007-02-17
> **ukripper said:**
> Are you putting xserver-xorg or xserver-org?

Make sure command should be as below exactly:

**$ sudo dpkg-reconfigure xserver-xorg**


Thank you for catching that. I tyoed it in correctly this time and it started. I went through and answered the questions with what I thought were the correct answers, but now it gets stuck at the black screen with Ubuntu and the orange progress bar. There is a dotted blue and a dashed green line accross the screen when it stops. It will let me ctrl+alt+del to restart, so I don't think it is locked up. Is there a list or something that shows what I should be putting in the xorg file?

---

### Post by ukripper on 2007-02-19
> **mikeescott said:**
> Thank you for catching that. I tyoed it in correctly this time and it started. I went through and answered the questions with what I thought were the correct answers, but now it gets stuck at the black screen with Ubuntu and the orange progress bar. There is a dotted blue and a dashed green line accross the screen when it stops. It will let me ctrl+alt+del to restart, so I don't think it is locked up. Is there a list or something that shows what I should be putting in the xorg file?

use that command again and try using **VESA** drivers at very first option of xorg configuration and select rest leave the defaults as it reconfigures.

By the way are you using CRT, LCD or laptop?

---

