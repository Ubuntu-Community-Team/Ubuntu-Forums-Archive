---
title: "java problems"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by bac2nowere on 2007-08-18
I am very new to using Ubuntu. I just installed Ubuntu 7.04. Everything works fine except I can't view anything that requires java. I have tried various other helps from other threads but I haven't had any luck. When I try to down load the plug ins it says download manually. When I try this it gives me an error saying that the association helper does not exist.


Any help and wisdom on how to solve this problem would be greatly appreciated.

---

### Post by Jimmyfj on 2007-08-18
Try this command:

 sudo apt-get install ubuntu-restricted-extras

Else there's plenty of Java in Add/Remove to be installed

---

### Post by bac2nowere on 2007-08-18
Thanks for such a fast reply.
I tried the command. I get this.
[PHP]chad@chad-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chad@chad-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
chad@chad-desktop:~$ 
[/PHP]

What is a superuser privilege and how do I change this? I have seen before but I didn't know what to do.

---

### Post by Armman on 2007-08-18
type in sudo before the command. This will give you root privileges (root=superuser)

---

### Post by Gremlinzzz on 2007-08-18
sudo dpkg --configure -a
java is in synaptic package manager

---

### Post by capink on 2007-08-18
Try this:

[http://ubuntuforums.org/showthread.php?t=522008]("http://ubuntuforums.org/showthread.php?t=522008")

---

### Post by bac2nowere on 2007-08-19
Thanks all. I got java up and going.=D>

---

