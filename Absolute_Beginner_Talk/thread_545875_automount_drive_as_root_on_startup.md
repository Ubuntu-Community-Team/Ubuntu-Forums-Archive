---
title: "automount drive as root on startup?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ign on 2007-09-08
I have a second drive on my PC, when I log in I can see it on the desktop, but when I click on it I'm asked for my password to access. The thing is i use this machine as a home file server, and all the media is in that second drive. Is there an easy way to have that drive working when I log without asking for the password?

---

### Post by overdrank on 2007-09-08
> **ign said:**
> I have a second drive on my PC, when I log in I can see it on the desktop, but when I click on it I'm asked for my password to access. The thing is i use this machine as a home file server, and all the media is in that second drive. Is there an easy way to have that drive working when I log without asking for the password?

Hi maybe this link will help
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) 
Good luck! :KS

---

### Post by ign on 2007-09-12
thanks for the reply.
this tutorial seems a bit outdated, so i didn't follow it. i don't feel comfortable messing with config files.
the drive actualy appears on the desktop at startup, i just have to put my password every time i turn on the computer in order to access it. isn't there an easier way (through the gui) to do this?

---

### Post by psusi on 2007-09-12
You need to edit /etc/fstab like the tutorial says.  Only make the mount point /media/foo instead and it will show up as "foo" on your desktop.

---

### Post by ign on 2007-09-15
thanks for the tip. i'll give it a try :)

---

### Post by ign on 2007-09-16
Let me ask another newbie question: how can I launch an application at startup? (in this case it's mt-daap which i use to share my mp3 library, must be started from the command line).

---

### Post by idiotonuni on 2008-02-12
If you are now running ubuntu 7.10 gutsy gibbon you can go to system preferences and sessions to set programs for startup.

---

