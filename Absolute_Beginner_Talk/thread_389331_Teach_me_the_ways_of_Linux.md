---
title: "Teach me the ways of Linux"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by buddahbelly on 2007-03-20
So I just put ubuntu on my compy and I cannot figure out how to use software like blender and audacity, or access my hard drives. It says stuff like "connot mount selected volume" or "Not enough memory" or "you don't have permision" So I would like to know if there is an easy way to use this OS so I can use blender, or just play a gameand accsess my other hard drives.

Buddah:guitar:

---

### Post by Scheater5 on 2007-03-20
Your troubles with "mounting" and "permission" likely stem from the linux notion of a "root" account.  What Windows refers to as Administrator, Linux refers to as the root account.  In order to do anything that could potentially damage your system, you must be root.  In Windows most users rarely see this, because the default account is Administrator and most people never see a need to change this.  
The short answer is that you need root privliges to do mount drives.  
The "Ubuntu" answer is that the root account is disabled by default.  In order to access root provilges, you issue commands with the "sudo" command.  i.e.

> $ sudo mount /dev/sda1 /mnt/windows
in a command line.  (like Terminal, assuming you use Gnome)

This will then prompt you for a password.  Enter the password of the first account you created when you installed.  If you give us specific problem, we can give you more specific help.

---

### Post by aysiu on 2007-03-20
Read these links:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

