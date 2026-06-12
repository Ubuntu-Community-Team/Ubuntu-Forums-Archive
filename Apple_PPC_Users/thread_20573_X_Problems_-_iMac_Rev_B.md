---
title: "X Problems - iMac Rev B"
date: 2005-03-17
forum: Apple PPC Users
---

### Post by del914 on 2005-03-17
I have installed Ubuntu Warty on a iMac Revision B. The install went fairly well. I have had problems out the wazoo to get X to start. My last few problems included:

I got into X windows and saw my desktop but I got a GNOME Settings Daemon error saying that once I got it fixed I should restart GDM. 

I got another error message for Nautilius saying something about Bonogo...

I got multiple error messages saying that it couldn't start some of the desktop applets like the clock, desktop switcher, and tash can, etc...

I used Synaptic Package Manager to install Bonogo because it wasn't. I then restarted the machine. I finally got to a graphical login (before I wasn't seeing that I had to start x manually). But now when I login, it acts as it is starting up (hard drive starts kicking away) but then it kicks me back out to the login screen again.

I have tried failsafe GNOME and that doesn't work either. 

Any ideas?

-- del914

---

### Post by farruinn on 2005-03-21
Did you experience all of these problems immediately after installing?  If so then something terribly wrong happened during the install.  With the default install you shouldn't be missing any of these things (Bonobo, applets, etc).  Make sure you have the ubuntu-desktop package installed, that will insure you have all of the default applications installed.  Also, do you get any feedback when trying to log into one of the GDM sessions?  A splash screen, error message, anything?

Also, with Ubuntu you shouldn't use startx to start the X server.  Instead use the /etc/init.d/gdm script.  To start X run 'sudo /etc/init.d/gdm start', to stop 'sudo /etc/init.d/gdm stop'.  GDM should start automatically though...

Hopefully we can help you more!  8-[ 
-Nathan

---

