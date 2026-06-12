---
title: "downloads"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Terrigal on 2008-03-28
Failed to run gdebi-gtk '--non-interactive' '/home/terrigal/Desktop/google-desktop-linux_current_i386.deb' as user root.
This is the message I get when ever I try to download a program.  Can anyone help?

---

### Post by Tatty on 2008-03-28
I have never seen that message before, but it sounds like you might be trying to open the deb in gdebi without root privilages.

How are you downloading the file?

If you are downloading from firefox make sure you click "save" before you click "ok", as firefox might default to try to open the file.

---

### Post by Terrigal on 2008-03-28
I tried to download google desktop for linux.  but have had the same experience with other downloads

---

### Post by lswest on 2008-03-28
```
sudo dpkg -i /home/terrigal/Desktop/google-desktop-linux_current_i386.deb
```
try that line in the terminal, should work.

---

### Post by Tatty on 2008-03-28
did you make sure you clicked "save" first?

But you dont need to download it from the webpage, it is available in the repositories.

**Edit: After reading lswest's reply i realised my stupidity, its clearly already downloaded. lol.**

---

### Post by Terrigal on 2008-03-28
Yes it has downloaded but fails to install because I get that message.

---

### Post by Terrigal on 2008-03-28
Here is the full message--Failed to run gdebi-gtk '--non-interactive' '/home/terrigal/Desktop/google-desktop-linux_current_i386.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by Terrigal on 2008-03-28
Here is the full message--Failed to run gdebi-gtk '--non-interactive' '/home/terrigal/Desktop/google-desktop-linux_current_i386.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by jimv on 2008-03-28
You can try what these guys tried:


[http://ubuntuforums.org/archive/index.php/t-334022.html](http://ubuntuforums.org/archive/index.php/t-334022.html)

---

### Post by Terrigal on 2008-03-28
I am literally an absolute beginner and much of what i see is mumbo Jumbo. Maybe there are programs/add on's that I have not installed.  Just got as far as I have from the Linux CD Have to go now.
Failed to run gdebi-gtk '--non-interactive' '/home/terrigal/Desktop/google-desktop-linux_current_i386.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

Where do I find gdebi-gtk 

Thanks

---

### Post by lswest on 2008-03-29
how are you trying to run this program?  Just double-clicking?  If so, try the command i posted above, which should install the package with super user privileges.  If that doesn't work, make sure your username is in the group "admin" (check this by going to system-->administration-->users and groups; then clicking "manage groups"; find admin, and make sure the checkbox next to your username is checked).

---

