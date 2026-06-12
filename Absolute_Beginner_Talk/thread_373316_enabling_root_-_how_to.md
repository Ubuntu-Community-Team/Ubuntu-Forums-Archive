---
title: "enabling root - how to"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by matrix13 on 2007-03-01
i installed ubuntu 6.10.
i read the 'root' is disabled by default.
so i was disappointed.
what is the 'root password'? or how can i change the 'root password' so that i can enable the 'root'
i tried lot. but failed each time. i was thinking to install another linux distribution.
then on a second thought i decided to try the forums before uninstalling...

is there any way for it. i dont like to use 'sudo' instead...
i want the complete control of my system.

---

### Post by anaconda on 2007-03-01
you can enable root account by giving root a password.. in terminal:
```
sudo passwd root
```
and then give the password you want.

EDIT: actually the above command asks first your own password and then it will ask the new root password.. You could first run "sudo ls" and then the above command so that your sudo password wont be asked again.. 


If you want to be able to graphical login as root you must also enable the root graphical login..
"System>administration>login window" and then from the security tab select 
Allow local system administrator login.

If I remember correctly.

---

### Post by koconnor100 on 2007-03-01
Don't enable root. you can trash your system real quick. 

The "sudo" command  means "super user do" and when you use it , that one single command is executed as if you were the root user, or super user. Use this instead , but only if you know what you're doing. There's probably a good reason why ubuntu isn't letting you delete all those files under the sys directory , stop and think about what you're doing before you use the sudo command.

---

### Post by jvc26 on 2007-03-01
You have complete control of your system, just there is an extra protection layer to stop you screwing it up and to stop malicious code running on it - typing 'sudo' or using 'gksudo' isnt that much effort for the extra security it gives you. After all its only one extra work when you're installing/uninstalling.
Il

---

### Post by geco on 2007-03-01
> **matrix13 said:**
> i installed ubuntu 6.10.
i read the 'root' is disabled by default.
so i was disappointed.
what is the 'root password'? or how can i change the 'root password' so that i can enable the 'root'
i tried lot. but failed each time. i was thinking to install another linux distribution.
then on a second thought i decided to try the forums before uninstalling...

is there any way for it. i dont like to use 'sudo' instead...
i want the complete control of my system.

2 useful links:

[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

byebye

---

### Post by aysiu on 2007-11-21
enabling root - why to?

---

### Post by petteriIII on 2007-11-21
Yep, there is very seldom reasons to act as root. But even normal text-editing may turn sour if you do it when you are root: every new file you create when you make text-editing is created as root as its owner. When you save it nothing says who owns it. Then some day later you backup your data - and because backups are usually operated on user-rights the backup-process quite calmly drops those files out - and weeks later you discover: where is part of my data ?

---

### Post by Perfect Storm on 2007-11-21
I lock this thread - as it was necromancing by someone promoting his blog. (in jail + ban).

---

