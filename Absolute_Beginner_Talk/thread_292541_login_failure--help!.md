---
title: "login failure--help!"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by benner on 2006-11-04
I have kubuntu running on a notebook as a dual doot with XP.  it was running just fine until i upgraded to edgy.  now, the login screen comes up, i type in my login and password, it tries to login, there's a black screen flicker and then it goes right back to the login screen again.  i only have 1 login set up.  i tried a different (wrong) one to see what would happen and it was different.  it immediately gave me a red 'login failed' error message.  i have continued to try the correct one and the same thing happens each time.  i can boot up with the command prompt but i'm not very familiar with too many commands to know what to do next.  i tried to just install it again with apt-get install kubuntu-desktop and (of course) it just told me that i already have the newest version installed.  do i need to reinstall it?  is there an easy way to sor tit out?  please help.

thanks...
-benner

---

### Post by K.Mandla on 2006-11-04
Something might have gotten hosed when you did the update. That black screen flicker is probably when it tries to jump to the desktop environment, then something craps out, so it drops back into the desktop manager.

See if you can get to a terminal window from your login screen (is that under the "Sessions" option?) and check your xorg.conf file. If it were me (and it's hard to guess what's going on otherwise), I would try changing the video driver option to "vesa" and see if X can start that way.

Again, that's a long shot and might not (probably won't) fix it, but that would be my first try.

---

### Post by Tamil on 2006-11-04
[Please Read if you experience a Blank Screen when booting Edgy LiveCD or Install](http://www.ubuntuforums.org/showthread.php?t=290655)

---

### Post by benner on 2006-11-04
from the login i can't get anything to happen.  i am restarting again in recovery mode and trying the following user's advice (we'll see if it works.  i do have an ATI graphics card which apparently is the problem.):

I read this on element14.wordpress.com. It was suggested by a posting on [http://www.planetmy.com/blog/](http://www.planetmy.com/blog/). It worked for me.

- When you get the blank screen upon bootup of Edgy, press enter to get a login prompt.

- Supply your user login and password.

- Then type the following: sudo apt-get install xserver-xorg

- Then type the following sudo rm /tmp/.X0-lock

That should solve the problem.

---

### Post by benner on 2006-11-04
didn't work.  xserver-xorg is already the newest version and the other one didn't exist.  still stuck...

---

### Post by benner on 2006-11-04
I'm still not having any luck.  Has anyone figured this out as it seems to be a problem for anyone with ATI graphics cards, I guess.  I get the splash screen as it boots up, I get the login screen, I type in my login and password and then the black flicker and then it returns to the login screen.      If I can use a different driver to get it running that would be great--only I have no idea how to do that...  Please advise...

---

### Post by botheredbybees on 2006-12-27
this is driving me crazy  - I've been using Edgy just fine for months on my thinkpad and suddenly I get this login problem

So far I've tried the following
running dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall xserver-xorg
sudo rm /tmp/.X0-lock
changed the xorg.conf 'ati' to 'VESA' (and back)
inspected /var/log/gdm/ log files and /var/log/Xorg.0.log for any suspicious activity (nothing found in either)
reinstalled GDM (sudo aptitude reinstall gdm gnome-session)
sudo apt-get remove xserver-xorg-video-ati and sudo apt-get install xserver-xorg-video-ati

all to no avail

I'm running out of things to try - any suggestions? ](*,)

---

### Post by botheredbybees on 2006-12-27
uh - one thing I should have checked: space on the home partition

seems my podcatcher had left a Christmas present there - every episode of every podcast I was subscribed to (well, right up until I ran out of disk space) - a few rm commands later and I'm back into gnome :p

---

