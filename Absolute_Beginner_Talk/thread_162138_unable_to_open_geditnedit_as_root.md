---
title: "unable to open gedit/nedit as root"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by vxj9219 on 2006-04-18
When i make myself root and try gedit or nedit, I get this message
(gedit:9302): Gtk-WARNING **: cannot open display:
NEdit: Can't open display
But I am able to open them as user with sudo. WHy isnt it working when I am root?

---

### Post by WoodyMahan on 2006-04-18
I am not an experienced Linux user, but it is my understanding that Ubuntu takes a slightly different approach to the root user from other distros.  Ubuntu is not really designed to run as the root user.  You will not find anywhere to setup or edit a password for the root user and 99% of us using it never need to log in as root and simply don't.  Using the sudo command you referenced is exactly how we get root level commands to run.  If I need to run an application as root then I use the command: gksudo <application> or create a launcher for the application using gksudo.  I know this doesn't exactly answer your question, but I believe the question might not be necessary because all root functionality is available when logged in as the user with the sudo command.  My primary log in is not "root".  It is the username and password I created when doing the Ubuntu install.  It is not a root user and does not have root access, but can perform functions as root when the sudo commands are utilized.  I think Ubuntu designed it this way to make it harder for us users to shoot ourselves in the foot.

---

### Post by vxj9219 on 2006-04-18
Thanks. I know I need not bother becoming root when I can use sudo, but I was just curious as to why gedit didn't work when I am root.

---

