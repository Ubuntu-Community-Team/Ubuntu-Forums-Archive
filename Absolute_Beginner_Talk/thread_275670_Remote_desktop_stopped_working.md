---
title: "Remote desktop stopped working"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by TheOldGuy on 2006-10-11
Ok.  I went to System>Preferences>Remote Desktop, etc and turned on remote desktop on Ubuntu.  Loaded TightVNC on my XP laptop.  Bingo.  Connected to Ubuntu.  What's the problem you ask?  That was yesterday.  Now it doesn't work.  I can ping the Ubuntu machine, I can access files through the network, but I can't run the desktop from the remote any more.  I unchecked the access then rechecked the boxes.  Rebooted both systems and even tried another VNC client on the XP box.  Still no connection.

Any suggestions?

---

### Post by Quintin Riis on 2006-10-11
Look at your desktop sharing settings again.  Make sure it is not set to 'ask for permission'.

Also, from the XP machine try to telnet to the port the VNC server is running on.  Should be 5800 or 5900.  Is it open or closed?

---

### Post by yariops on 2006-10-29
Hi I have a problem with remote desktop too

I configure the service and connected with another computer everything is OK but the problem is when i restart the computer I can't connect to the remote desktop because a problem of authentication... then i insert the pass again ... then retry and i  have access ... very strange....

Anyone with this kind of problem

Thanks and Best Regards

---

