---
title: "GUI stalls on start up (Oh no! NOW what have I done)"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-02
Okay I had been fiddling but with nothing major, just icons and stuff.  Restarted and was using windows to run a program when we had a power cut.

Turned PC back on and started up Ubuntu.  entered name and password and the GUI starts to load, the splash does it's thing and then I see my desktop image with two menu bars and then nothing and a crash back to the Ubuntu logon screen.

WHAT HAVE I DONE:confused: 

How can I fix it???

---

### Post by Roger_Melly on 2007-03-02
HELP:confused: :(

---

### Post by Roger_Melly on 2007-03-02
Please guys,
How do I diagnose and fix a boot up crash?

---

### Post by namelessone on 2007-03-02
first, try selecting rescue mode at the when grub starts up. You might have to press esc. to see this option.

Next, cd into the /var directory and look for log files of the crash. Log files can be scary, but you should see something in it that looks like semi-plain english that will tell you why it crashed in the first place.

---

### Post by Roger_Melly on 2007-03-02
Namelessone,
thanks.....
Real Noob here cd into the /var directory?

---

### Post by Roger_Melly on 2007-03-02
Okay,
I'm slowly becoming adept!

my crash file reads like this:

_usr_bin_Xorg.0.crash
_usr_bin_gnome-volume-control.1000
_usr_bin_beagled.1000.crash
_usr_lib_firefox_firefox-bin.1000.crash

the last thing I was doing when Ubuntu worked was trying to change the firefox icon.  Could this be the problem?  How do I remedy it.......

---

### Post by namelessone on 2007-03-02
Once you log into rescue mode you will be greeted with something like this:

root@localhost$

Welcome to the world of linux command lines.
type
```
cd /var
```
to change directories into the /var directory. This directory stores most of the log files. From here, type the ls command to list the things in this directory.
I'm not a linux guru, but I would guess that a log of what happened might be in the directory crash. cd into that directory and type ls to see if there are any log files.
You can read a log file by typing
```
less logfile
```
where logfile is the name of the log. Assuming you find a logfile that has X11 or gnome in it's name, post the very tail end of the log here and maybe that will help us solve your problem.

EDIT: i guess you answered your own question before I could answer it...anyway, i think the Xorg crash log is the one you want to look at. post the tail end of it here.

---

### Post by Roger_Melly on 2007-03-02
Okay these are my logs which one do I go for?


Xorg.0.log       cups            fsck                  scrollkeeper.log
Xorg.0.log.old   daemon.log      gdm                   syslog
Xorg.20.log      daemon.log.0    installer             syslog.0
acpid            debug           kern.log              syslog.1.gz
apport.log       debug.0         kern.log.0            syslog.2.gz
apport.log.1     dist-upgrade    lastlog               syslog.3.gz
apport.log.2.gz  dmesg           lpr.log               udev
apport.log.3.gz  dmesg.0         mail.err              unattended-upgrades
aptitude         dmesg.1.gz      mail.info             user.log
aptitude.1.gz    dmesg.2.gz      mail.log              user.log.0
auth.log         dmesg.3.gz      mail.warn             uucp.log
auth.log.0       dmesg.4.gz      messages              wtmp
boot             dpkg.log        messages.0            wtmp.1
bootstrap.log    dpkg.log.1      news                  wvdialconf.log
btmp             faillog         nvidia-installer.log
btmp.1           fontconfig.log  pycentral.log

---

### Post by Roger_Melly on 2007-03-02
Anyone please......

---

### Post by namelessone on 2007-03-02
> 
my crash file reads like this:

_usr_bin_Xorg.0.crash
_usr_bin_gnome-volume-control.1000
_usr_bin_beagled.1000.crash
_usr_lib_firefox_firefox-bin.1000.crash

look at the _usr_bin_Xorg.0.crash one.

---

### Post by Roger_Melly on 2007-03-03
Sorry namelessone I gave up and reinstalled.

I was so new to this that I had nothing to lose in doing so.
Prior to the crash I was changing the firefox logo and trying to move icons around the desktop.  On several occasions the Gnome foot kept appearing on the panel instead of whatever I was trying to drag.  I kept removing it.  I'm wondering if this had some effect on gnome.

For other Newbies out there do not despair.....

I remember getting windows and fiddling about with themes and downloading stuff to make it look pretty and it crashed all the time until I learnt to leave that well alone!

I am interested in learning more about commands and so forth though.

Thanks for your advice.

---

