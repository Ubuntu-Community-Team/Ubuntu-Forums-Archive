---
title: "external HD help"
date: 2008-08-12
forum: Apple Hardware Users
---

### Post by HakerDemon on 2008-08-12
hello,
      I have an a 500gb external hard drive that I want to use between my macbook pro, and my ubuntu desktop.  the desktop is running 8.04 and my macbook is running os x 10.5.  But my ubuntu desktop wont allow me to write anything on the drive, saying it does not have the rght permissions.  Does anyone know about how to change the positions so i can read and write with both computers?  thank you.

---

### Post by flaggh on 2008-08-12
If you formatted it with OSX, its probably formatted as HFS+ journaled.  Ubuntu cannot write to a journaled HFS+ drive.  You must either turn journaling off or use a different filesystem.  Search the forum for more information as there are plenty of posts concerning this issue.

---

### Post by cyberdork33 on 2008-08-12
> **HakerDemon said:**
> hello,
      I have an a 500gb external hard drive that I want to use between my macbook pro, and my ubuntu desktop.  the desktop is running 8.04 and my macbook is running os x 10.5.  But my ubuntu desktop wont allow me to write anything on the drive, saying it does not have the rght permissions.  Does anyone know about how to change the positions so i can read and write with both computers?  thank you.
I am assuming then that you have setup the hard drive with an HFS+ filesystem from your Mac? In this case, Ubuntu (like OS X) obeys file permissions as written. In the case of your files and folders on the drive created in OSX, they are "owned" by the user on OS X, thus, you do not have permission to access those folders with the user in Ubuntu.

You have a couple of options. You can connect back to OSX and set all the permissions so that other users can read/write as well, or you can create a user in Ubuntu that has the same userid (not name) as your OSX user. This way both OSs see the files as owned by your user.

Also note that you may not be able to write to an HFS+ partition unless journaling is disabled (done in OS X). 

Of course you can make all this really easy, and just format the external drive to FAT32.

---

