---
title: "KDE no shutdown option"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2008-01-09
I've read a few places that this could be cause by XGL, and there is a fix concerning startxgl.sh, but I can't find that file (not in /usr/bin/) .  Is it somewhere else, or is something else wrong?

---

### Post by john_spiral on 2008-01-09
do you have a log out option?

---

### Post by arochester on 2008-01-09
Have you got GDM rather then KDM? GMD will have the shutdown. KDM will have the logout.

---

### Post by CeeDub on 2008-01-09
I am using KDM.  The only option I have is the logout option.

---

### Post by OffAxis on 2008-01-09
what happens when you log out?
does it come back to the username/password login screen, shutdown, or kick out to a terminal?

---

### Post by CeeDub on 2008-01-09
It comes straight back to login screen.

---

### Post by MickS on 2008-01-09
I have the same problem, what I do is when in the log in screen go to the options thing and you will find a shutdown button at the bottom of the drop down list, click on that then you get another choice shutdown or restart. Tedious but you get there eventually


Mick.

---

### Post by CeeDub on 2008-01-09
I have just been going to terminal and using the shutdown command.  But that's annoying.  I woudl really like to fix this.

---

### Post by rhc on 2008-01-09
This is a funny problem.
Can't you close the computer? :p

---

### Post by CeeDub on 2008-01-09
I've made two quicklaunch icons.  One to shutdown and one to reboot, but I need to type in my password everytime.  It's really annoying.  Is there anything I can do to fix it.

---

### Post by OffAxis on 2008-01-10
I found this thread that might help.
[http://ubuntuforums.org/showthread.php?t=185275]("http://ubuntuforums.org/showthread.php?t=185275")

from the thread...
> I've found the options that should allow me to shutdown from the logout menu, but nothing changes when I change them to what I think they should be.

In Kubuntu Dapper, they can be found in **System Settings > KDE Components > Session Manager**

and
> SUCCESS!!!

Under Settings > Login Window > Local tab, I had Show Actions Menu unchecked, now all is well.

I'm not sure if that last one is for kde or gnome, but I hope it helps.

---

### Post by CeeDub on 2008-01-10
I've been to that session manager and have checked the approptiate boxes, but I can't find the "Settings > Login Window > Local tab".  It may have changed since Dapper.  (I'm using Gutsy 7.10)

---

### Post by OffAxis on 2008-01-11
kde4 is out today, maybe that'll take care of it for you.

---

