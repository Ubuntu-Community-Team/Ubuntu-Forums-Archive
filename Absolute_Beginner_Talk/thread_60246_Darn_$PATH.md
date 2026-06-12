---
title: "Darn $PATH"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by RobArson on 2005-08-27
Some background: 
I'm dual booting XP and ubuntu on my XP with a third 5GB partition using fat32 so I can transfer files inbetween XP and ubuntu.

I have changed etc/fstab so that the partition mounts everytime i log in.

I want to put the directory mounted to the 5GB partition in my path, so I went to etc/bash.bashrc per instructions I've seen on the web and did the following:

PATH=$PATH:/shareddrives
export PATH

(shareddrives is the name of the directory mounted to the 5GB shared partition)

I restarted, but still no luck in running "itsacfile", a file compiled from itsacfile.c

it worked when I simply did the command: export PATH=$PATH:/shareddrives
but i want something more permanent.

Any advice would be appreciated, thanks!

---

### Post by amohanty on 2005-08-27
Try putting this in .login in yout home dir. I think it shouldnt be there by default so make one.

HTH
AM

---

### Post by numberexhaust on 2005-08-27
What you need to do is open the following file:

sudo gedit ~/.bashrc

and insert the export line at the bottom of the file.  Why this works is because when you export the variable, it does it only for the current session.  If you want the change to be permanent, you put it in this file, which is executed every time you start a terminal.

---

