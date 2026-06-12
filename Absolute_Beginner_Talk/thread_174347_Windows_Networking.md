---
title: "Windows Networking"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2006-05-11
I'm having trouble networking from my ubuntu laptop to my XP desktop.  I'm trying to transfer all the important files from my laptop.  I can't seem to get either machine to recognize the other.  I've done this before but I don't remember how I did it or if something changed since then that would affect this.  Now I'm linked through a router and the Windows Network folder shows nothing in it.  I'm pretty sure it's just a minor thing I overlooked but I don't know, any help would be much appreciated.
Thanks,
Nolan

---

### Post by linuxcity on 2006-05-11
First, make sure that you are in the same network, that you can ping each other. Second, you need to share a folder in your Windows XP. Third, install Samba on the Linux machine if you haven't done so. Once Samba is install, you can connect it using  "Places | Connecto to Server" and fill out the information of the Windows XP machine.

---

### Post by linuxcity on 2006-05-11
First, make sure that you are in the same network, that you can ping each other. Second, you need to share a folder in your Windows XP. Third, install Samba on the Linux machine if you haven't done so. Once Samba is install, you can connect it using  "Places | Connecto to Server" and fill out the information of the Windows XP machine.

---

### Post by madddonkey255 on 2006-05-26
The problem was that firestarter was blocking the windows machine.  Now I have access to the windows computer but when i try to copy and paste the folders I get an error message that just says "Access Denied", the folder isn't write protected the files also aren't.  I don't know what to do now.
Thanks, 
Nolan

---

