---
title: "What is Sudo?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-19
I've seen a lot of advice that involves using sudo in terminal, and I've used sudo a lot when I install new things. What is sudo (in depth explanation please)?

---

### Post by voodoonirvana on 2006-09-19
(s)uper (u)ser (do)

use it when it wont give you permission in the terminal

---

### Post by mongooseman1128 on 2006-09-19
oh okay. So it's for over riding file permissions?

---

### Post by jISh on 2006-09-19
sudo gives the command root authority. Ubuntu protects your system by locking you out of root/core files and only allowing you access to your home folder/files. 

Most installs and such require root authority to modify the root files/folders so you are asked to put sudo in front of the command.

---

### Post by aysiu on 2006-09-19
It temporarily allows you to execute a command with root privileges, even though you're logged in as root.

For example, if I type these commands: ```
cd ~/Desktop
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo cp sources.list /etc/apt/sources.list
rm sources.list
``` the first two commands are operated with user privileges. The third command is operated with root privileges. The last command is user again.

Using the root model instead, you would do this: ```
cd ~/Desktop
wget -c http://www.psychocats.net/ubuntu/sources.list
su
cp sources.list /etc/apt/sources.list
exit
rm sources.list
```

---

### Post by mongooseman1128 on 2006-09-19
oh... is that why I couldn't add a file to /etc/apt it wouldn't let me? would I need to save the file using a sudo terminal command?

---

### Post by aysiu on 2006-09-19
You would need to open it with a *sudo* command--something like ```
sudo nano -B /etc/apt/sources.list
```

If you prefer to do it the point-and-click way, press Alt-F2 and type ```
gksudo nautilus
```

---

