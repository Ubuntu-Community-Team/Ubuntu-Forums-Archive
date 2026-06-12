---
title: "a few questions"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by supernoob on 2007-12-22
Hi all, although it's nice that Ubuntu cares about security and asks for a password for many things , there are two things I would like it... not to - the first is - when I type "sudo cable-start" (that's a command for a script i use to connect to the internet).

the second is - although I installed Ubuntu using wubi, i have a second hard drive and as I use it for downloads and i don't want being have to open it with file browser and entering a password each time before starting a download.

another minor question is - how can I put the trash on the desktop?

---

### Post by jken146 on 2007-12-22
> **supernoob said:**
> Hi all, although it's nice that Ubuntu cares about security and asks for a password for many things , there are two things I would like it... not to - the first is - when I type "sudo cable-start" (that's a command for a script i use to connect to the internet).
You could make the script executable for your user.

> the second is - although I installed Ubuntu using wubi, i have a second hard drive and as I use it for downloads and i don't want being have to open it with file browser and entering a password each time before starting a download.
You should create an entry for this drive in /etc/fstab -- I'm sure you'll find a How To on these forums.  I think there is a guide for this on psychocats.net too.

> another minor question is - how can I put the trash on the desktop?
Hit Alt+F2, type in **gconf-editor** and press enter.  Navigate to Apps > Nautilus > Desktop and there is a tick box for displaying the Trash.

---

### Post by supernoob on 2007-12-22
Tnx for the replay, BUT- apparently I don't have the "/etc/fstab" folder, should I make one ?, also i don't have a clue how to "make the script executable for your user."

---

### Post by jken146 on 2007-12-22
/etc/fstab is a text file that tells Ubuntu which partitions to mount automatically and where.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) should help you.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) might help you with file permissions.

---

