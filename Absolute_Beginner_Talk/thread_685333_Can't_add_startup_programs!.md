---
title: "Can't add startup programs!"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by tangibleorange on 2008-02-02
Hello,

When I try to add startup programs to the startup menu, they add fine, and then when I go back into later they are gone. In other posts, there is a fix detailing that I need to change the permissions of /.config/autostart.
But here's the weird part. That folder doesn't exist for me... I do 'gksu nautilus', turn on hidden files, navigate to that directory, and there's no folder or file called autostart. The command

> sudo chown /home/USER/.config/autostart

seems to go through OK (no errors) but nothing changes.

Does anyone have any ideas?

---

### Post by mac71 on 2008-02-02
I think , if you're using ubuntu you just goto system>preferences>session and add your perfered app there ie; aMSN with the command /usr/bin/amsn

Autostart is how you do the same thing in kubuntu.

Hope thats of some help.

---

### Post by tangibleorange on 2008-02-07
Solved by doing a fresh install. Don't know what happened there...

Thanks anyway!

---

### Post by rudder on 2008-05-04
I just ran into this myself after an upgrade to 8.04 from 7.10.  One of my users' lost their autostart folder.  I found two things that were out of the ordinary.  First, there was a **file** named "autostart" under the .config folder for that user.  It would not show up in nautilus though, even with the hidden files shown.  Second, the owner and group on this file were "root".  I tried "sudo chown <username>:<username> autostart" (where <username> is the name of your user).  The command went through but the issue was not resolved.  

Autostart has to be a folder so I just removed the file "autostart" and placed a folder there instead.  Make sure the user in question has ownership and read/write to the folder.  Once that is done, you should be good to go.

Also, you could probably just copy the autostart from another user (if any) and drop it in there... probably just easier to recreate the folder.

Hope this helps!

---

