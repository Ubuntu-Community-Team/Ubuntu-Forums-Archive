---
title: "I can't update"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by austinw on 2006-09-04
I installed ubuntu last night.  (linux virgin)
When I click on the update button a box opens telling me, Only one software management tool is allowed to run at the same time.  I never ran any software management tool that i know of.  I have rebooted and still get the same message. Can anyone help?

---

### Post by Anonii on 2006-09-04
Never really used the GUI update tools, so I'll guide you to the precious Linux command line (gotta love it :] ).

First of all, open the terminal.
Execute the command: *sudo aptitude update*
And then: *sudo aptitude dist-upgrade*
And then: *sudo aptitude upgrade*


This will lead you to an upgraded system, like Synaptic would.
Good luck :]

---

### Post by xyz on 2006-09-04
This usually happens when you click on the update button AND Synaptic is running as well which is why it says "Only one software management tool is allowed to run at the same time".
Are you sure Synaptic isn't running as you try to update via the button?

---

### Post by austinw on 2006-09-04
XYZ >  I have never rand synaptics.  Also, when i check System Monitor it doesn't show up.


Anonii > I get this message when i try sudo aptitude update: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
then it tells me: dpkg --configure -a
dpkg: requested operation requires superuser privilege

---

### Post by austinw on 2006-09-04
could automatix be causeing a problem w/ this?  The person that recommened ubuntu told me to run it after i install.  It doesn't appear to be running now. (after several reboots)

---

### Post by Anonii on 2006-09-04
> **austinw said:**
> XYZ >  I have never rand synaptics.  Also, when i check System Monitor it doesn't show up.


Anonii > I get this message when i try sudo aptitude update: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
then it tells me: dpkg --configure -a
dpkg: requested operation requires superuser privilege
Use: sudo dpkg --configure -a 

And then the other commands I said before.

> could automatix be causeing a problem w/ this? The person that recommened ubuntu told me to run it after i install. It doesn't appear to be running now. (after several reboots)

No, automatix isnt causing this. Dont worry :)


Also, after we fix this problem be sure to read this:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
and this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by xyz on 2006-09-04
Also could this maybe be the pbm? Lots of people have had problems with this lately.
PLEASE READ: The Latest Updates Break the Xserver!
[http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

---

