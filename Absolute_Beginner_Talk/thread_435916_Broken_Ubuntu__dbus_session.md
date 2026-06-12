---
title: "Broken Ubuntu ? dbus session ??"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-05-07
Everything has worked ok until now. When I shudown my computer this morning it was working ok. I have just tried to start again I get to the login secrren and log in ok but then get the message 
" Your session only lasted less thank 10 seconds. If you have not logged out yourself it could mean that there is an installation problem or you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem."

I logged in with the Gnome failsafe and everything seemed to be ok I get the desktop and all the folders etc. but then get a message "Power manager cannot start until you start the dbus session service"

Where do I go from here to fix the problem. I do not know what the problem is even.

Thanks 
Roy

---

### Post by dstew on 2007-05-07
What version of Ubuntu do you have? Does this problem occur every time you boot, or did it only happen once?
The error means that the Power Manager application needs the dbus daemon to run, and it could not find the dbus daemon. It could be an installation problem, that is, dbus is not installed, or if it is installed, it is not starting at boot time.
You can check to see if dbus is installed by entering **dbus-daemon --version** on the command line.

---

### Post by roylond on 2007-05-07
Hi dstew
I'm using 6.06 Dapper 
The problem only arose today and happens everytime I boot and log in
I checked the dbus daemon installation in the command line  dbus-daemon --version
The reply is     D-BUS Message Bus Daemon 0.60

Thanks 
R

---

### Post by dstew on 2007-05-08
OK, dbus is working.

I looked around and found [this thread.]("http://www.linuxquestions.org/questions/showthread.php?t=386010") It looks like the problem will turn out to be that your home directory has been misidentified as /root, so that when you log in, it cannot start, since you will not have root privleges. It is also possible that your .gnome directory in your home directory has had its permissions changed. The thread contains some suggestions as to possible fixes. Try the fix suggested by royjones first (look at the home directory in your user account). I can help you with some of the others too.

EDIT: Here is [another thread]("http://marc.info/?l=gnome&m=112760670403796&w=2"). The problem in this case was altered permissions in the .ICEauthority file.

---

