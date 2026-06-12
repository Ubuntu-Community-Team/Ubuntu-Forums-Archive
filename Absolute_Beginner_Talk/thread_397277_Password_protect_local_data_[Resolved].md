---
title: "Password protect local data? [Resolved]"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-03-30
Is there a good way to set passwords on specific folders? Let's say I have some data I don't want people accidentally accessing, is there a way I can set a password on just that folder or group of folders?

---

### Post by aysiu on 2007-03-30
You could just change permissions on those folders so only the owner can read/write/execute them: ```
sudo chown -R lamalex:lamalex /path/to/folder
sudo chmod -R 700 /path/to/folder
```

---

### Post by lamalex on 2007-03-30
That's not a great fix as I'm the only user on this computer, so anyone who uses this computer is on as me. It's my personal laptop but my mom and brother use it whenever I'm home because a) they seem to be taking a liking to ubuntu over windows and 2) they don't want to be in the computer room. I don't really want them stumbling across some files, I've already hidden the folder with a . but i'd like another level of security. And I know you're all thinking it's pr0n, it's not.

---

### Post by Maestro23 on 2007-03-30
Could also just create a user account for them to use and specify what they have access to.

---

### Post by lamalex on 2007-03-30
So what I'm getting from these posts is "no there's no good way to password protect a folder."

---

### Post by aysiu on 2007-03-30
Then make root the owner: ```
sudo chown -R root:root /path/to/folder
sudo chmod -R 700 /path/to/folder
``` You can then access the files with *gksudo nautilus* and a password entry, or if you prefer a right-click thing, I believe there's a Nautilus script for "open as root here."

By the way, it's not that difficult to set up a guest account for mom and brother.

---

### Post by lamalex on 2007-03-30
Yeah I know. I technically made my mom an account, she just doesn't use it since she knows my password.

---

### Post by aysiu on 2007-03-30
I still think giving root ownership and changing permissions is the easiest way to do it, but for alternative methods, check out these threads.
[Password Protect One Folder inside Another Folder](http://ubuntuforums.org/showthread.php?t=89354)
[password protect folder/files?](http://ubuntuforums.org/showthread.php?t=25848)

---

### Post by lamalex on 2007-03-30
that open as root script sounds perfect actually. :) thanks for that tip, I always forget that nautilus is highly extensible.

---

### Post by aysiu on 2007-03-30
> **Iamalex said:**
> that open as root script sounds perfect actually. :) thanks for that tip, I always forget that nautilus is highly extensible.
This HowTo will get you up and running on that:
[HOWTO: Easily open any file as root via drag & drop](http://ubuntuforums.org/showthread.php?t=24008)

---

### Post by lamalex on 2007-03-30
Yeah I followed the right click one from ubuntu guide and it is perfect, for some reason when it asks for root password it takes my user password, not the actual root user password.

---

### Post by aysiu on 2007-03-30
> **Iamalex said:**
> Yeah I followed the right click one from ubuntu guide and it is perfect, for some reason when it asks for root password it takes my user password, not the actual root user password.
That's because Ubuntu, rather than enabling a direct root login, uses something called *sudo*, which allows users in the admin group to temporarily assume root privileges with a password authentication.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lamalex on 2007-03-30
Yeah, I understand sudo, I just didn't know its scope.

---

### Post by Kale on 2007-04-05
so i was kinda stupid, and accidentally applied the following code to my home folder

sudo chown -R root:root /path/to/folder
sudo chmod -R 700 /path/to/folder

as you can imagine my entire system is locked up now, any suggestions on digging myself out of this hole? thanks                                    -Kale

---

### Post by aysiu on 2007-04-05
Yikes. the change of ownership isn't that bad, but the change of permissions to 700 for everything is bad.

Your best bet is to create a new user and then copy over your personal files. 

Boot into recovery mode and type ```
sudo adduser *nameofnewuser*
sudo adduser *nameofnewuser* admin
reboot
``` Log in as the new user, press Alt-F2 and type ```
gksudo nautilus
``` for Ubuntu (if you're using Kubuntu, *kdesu konqueror*; if you're using Xubuntu, *gksudo thunar*) and copy all your /home/*oldusername*/important personal files to /home/*newusername*/important personal files.

Then do ```
sudo chown -R newusername:newusername /home/newusername
``` Do not do a *chmod*, though.

Finally, make a backup copy of and then edit as root the /etc/groups file and make sure your new username is in these groups: ```
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner
``` If you don't know how to edit as root, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Kale on 2007-04-05
thank you so much. That was VERY helpful. ^_^ My comp is happy again.

---

### Post by Kale on 2007-04-06
Im up and running, everything is all better!!

---

