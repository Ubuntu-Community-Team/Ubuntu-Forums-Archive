---
title: "PATH setting"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by chadmichael on 2006-03-16
I set the PATH variable in /etc/profile.

If I login to the console, this is reflected in my environment.  I can find the PATH that I set. 

However, when I go into the gnome graphical session, the PATH doesn't relfect the changes I made in /etc/profile.  Even when I open a terminal from within gnome, I don't see the change.

IS gnome overiding my /etc/profile settings?

Is gnome ignoring /etc/profile?  
Even when I start a terminal from within gnome?  

thanks

---

### Post by oakz on 2006-03-16
Once gdm is started (the login manager and parent process of gnome-session) you cannot change that processes PATH as it read it from /etc/profile at system startup time.
Log out of gnome and back into a console, and type:

$ sudo /etc/init.d/gdm restart

When X restarts try logging in, your PATH changes should be set.
If you want to tailor PATH settings for only your user, place them in ~/.bashrc or ~/.profile (see "man bash" for details), and when you launch a terminal in GNOME your PATH changes will be included in that bash session.

---

