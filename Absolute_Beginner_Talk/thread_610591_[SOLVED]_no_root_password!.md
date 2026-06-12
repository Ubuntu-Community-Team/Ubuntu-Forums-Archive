---
title: "[SOLVED] no root password!?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by thenailedone on 2007-11-12
I installed Feisty 64-bit last night...

Had a read [here]("http://ubuntuforums.org/showthread.php?t=136367") but my problem is I never created (and can't remeber being given the option) a root password... so what now?  

:confused:

---

### Post by kellemes on 2007-11-12
You don't need to login as root.. just use Sudo.
Sudo asks for **your** password.
[https://help.ubuntu.com/community/RootSudo?highlight=%28root%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28root%29")

---

### Post by Paqman on 2007-11-12
You don't need a root password for Ubuntu. Any time you need root priviledges you can elevate yourself using the sudo command (or gksu/kdesu for GUI aps) and you own password.

---

### Post by steve.horsley on 2007-11-12
Use sudo when you need super privilege. Read here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by iomnipwnedyou on 2007-11-12
when in doubt, use sudo

---

### Post by Sukarn on 2007-11-12
If you need to run a lot of commands as root then just use "sudo su" which will start a root shell when you give it your own password.

---

### Post by thenailedone on 2007-11-12
... last time I touched Linux it was all about root and the password...

Thx to all :lolflag:

---

### Post by snakep on 2007-11-14
I'm coming from Suse, and there I need a root password to do anything.  Now, I've found that I'm asked for a root password to install updates with the GUI.  For example, when I logged on, there was a notification that updates were available.  When I clicked the icon and tried to start the installation, it asked for a root password.  I tried my own password, and it didn't work.  Any ideas?

---

