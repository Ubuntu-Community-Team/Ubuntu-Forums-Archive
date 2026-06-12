---
title: "Xscreensaver instead of Gnome-screensaver"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by sYs^ on 2006-04-14
Hi,

I'd like to use xscreensaver instead of the default gnome-screensaver, I installed xscreensaver with apt-get and some extra packages, but still gnome-screensaver starts on boot how could I change it to xscreensaver?

Thank you in anticipation...

---

### Post by patrick295767 on 2006-04-14
[QUOTE=sYs^]Hi,

I'd like to use xscreensaver instead of the default gnome-screensaver, I installed xscreensaver with apt-get and some extra packages, but still gnome-screensaver starts on boot how could I change it to xscreensaver?

Thank you in anticipation...[/QUOTE]
 
i would propose you to remove/uninstall gnomescreensaver
 
apt-get -f -y install xscreensaver 

to run it : 
xscreensaver -nosplash
 
to configure it : xscreensaver-demo

Greetz

---

### Post by sYs^ on 2006-04-14
Thanks for the answer!

I have xscreensaver already installed, if I start xscreensaver-demo, it writes xscreensaver daemon is not running (so it doesn't start by default).

If I try to remove gnomescreensaver 
```
dani@ubuntu:~$ sudo apt-get remove gnome-screensaver
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  gnome-screensaver **ubuntu-desktop**
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 3326kB disk space will be freed.
Do you want to continue [Y/n]?
```

It wants to remove ubuntu-desktop too and that would be bad for me, imho :>

---

### Post by hw-tph on 2006-04-14
Removing ubuntu-desktop isn't much of a deal. ubuntu-desktop is a huge metapackage that lists all the default components of the Gnome Ubuntu desktop as dependancies, and by removing gnome-screensaver you are breaking ubuntu-desktop. If you want to remove the asian font packs installed by default (they do take up quite a bit of space - oh, and Emacs begone!) the ubuntu-desktop package will break too.

Since packages are updated anyway when new versions arrive in the repositories this doesn't change the behaviour of your system at all.


Håkan

---

### Post by sYs^ on 2006-04-14
Wow, thank you, I didn't know this. I thought that's something serious :>

Then there's still one more quesion, how could I start xscreensaver daemon on boot time?

**_Edit_**: Ups, I figured out: xscreensaver -no-splash 

Thanks for your help guys!

---

### Post by patrick295767 on 2006-04-14
[QUOTE=sYs^]Thanks for the answer!

I have xscreensaver already installed, if I start xscreensaver-demo, it writes xscreensaver daemon is not running (so it doesn't start by default).

If I try to remove gnomescreensaver 
```
dani@ubuntu:~$ sudo apt-get remove gnome-screensaver
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  gnome-screensaver **ubuntu-desktop**
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 3326kB disk space will be freed.
Do you want to continue [Y/n]?
```

It wants to remove ubuntu-desktop too and that would be bad for me, imho :>[/QUOTE]
  
to run xscreensaver daemon: 
just type : 
```
xscreensaver 
```

 Grreetz

---

### Post by detyabozhye on 2006-04-21
how can I have both installed but use xscreensaver as default?

---

### Post by detyabozhye on 2006-04-22
OK, I unchecked these keys in gconf-editor:
/apps/panel/global/disable_lock_screen
/apps/gnome_settings_daemon/screensaver/start_screensaver

I disabled gnome-power-manager in startup programs and added xscreensaver -nosplash to startup programs.

And since I run XFWM instead of Metacity, I added xscreensaver-command -lock to my keyboard shortcuts.

I know it's a lousy method, but oh well, it works.

Edit: changed gconf to gconf-editor, sorry for confusing everybody.

---

### Post by vayde on 2007-12-02
this was for Dapper, but it may still work

[http://ubuntuforums.org/showthread.php?t=195557&highlight=Screensaver](http://ubuntuforums.org/showthread.php?t=195557&highlight=Screensaver)

good luck

---

