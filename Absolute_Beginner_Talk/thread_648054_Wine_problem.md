---
title: "Wine problem"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by mLes-_- on 2007-12-23
I am having problems with the Wine program.  I want to use it for Ventrilo and CS 1.6.  I installed it and when I go to Applications>Wine>Configure Wine I can hear my HDD reading it and then all of a sudden my PC locks up and freezes.  Any suggestions or things I should post?

---

### Post by TeaSwigger on 2007-12-23
First off, if you don't already know, a linux tip to reboot a "frozen" system is in this thread:
[http://ubuntuforums.org/showthread.php?t=315404](http://ubuntuforums.org/showthread.php?t=315404)
though another thing to try is to "kill" the current session and return you to the login:
ctrl+alt+backspace
then try the above if it's a no-go.

Anyway, about this bad WINE. First is the install ok. Some questions: was this installed from the repositories or some other way? Was there a prior installation of it? Did this occur before or after you installed said programs (a bit unclear on the order from your post)? 

istr the WINE folks saying most freezes are caused when WINE finds a less than perfect graphics setup and ends up causing a freeze, otherwise, since it's running user-level, it shouldn't be able to freeze the system. So have you noted any graphics problems otherwise? Say sluggishness "drawing" or a less than great pic or the pic being off center so you had to tweak the monitor? If there's a chance of an issue there, please post your video card and what's in /etc/X11/xorg.conf any someone may be able to help you pin the prob.

---

### Post by inertz on 2007-12-23
For Ventrilo you might want to refer winehq website:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3668](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3668)

And CS
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507)

You also want to check out the commercial version of Wine here:

[http://www.transgaming.com/](http://www.transgaming.com/) for games

[http://www.codeweavers.com/](http://www.codeweavers.com/) for application

---

