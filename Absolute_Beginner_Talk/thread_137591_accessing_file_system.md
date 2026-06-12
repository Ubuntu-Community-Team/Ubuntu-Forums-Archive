---
title: "accessing file system"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by illusion on 2006-02-28
Hey,

I was trying to find out how you access the file system, I believe it is nuatilus, as a different user.  I would like to access the system as root so I have permission to change files.  Secondly, how to access the file system from the "/" level in terminal, so I would be able to access a directory such as "etc".

Any help would be appreciated,
thanks in advance,
Illusion

---

### Post by ubuntumaneh on 2006-02-28
I don't think I have understood your question. Let me give you some hints, then:

I use terminal a lot (like xterm, rxvt, gedit, konsole, it is your choice). If I want to use as a root, I type:

sudo su -

Now, for navigating in the filesystem use cd, ls and the likes. You can modify things in "/" only if you are root. You can be in the enviromment of root, as the above command gives you, or you can use each command preceded by sudo.

Is this ok?

---

### Post by illusion on 2006-02-28
Hey,

For example, say I want to access the etc/network/options.txt file.  My probelm is I dont know how to access it through terminal.  Even when I become root through sudo -i or sudo su -, I only have access to the as root user to the root directory.  How to navigate through the other directories?  I'm sure there is a really simple answer, just not seeing it.  Also all the files I access through nautilus or the gui, I dont have permission to change because I'm accessing it as another user and the owner of the file is root.  But you cant log in as root on the login screen when I try.  So how can I access those files as root user in the gui?

thanks again,
Illusion

---

### Post by ubuntumaneh on 2006-02-28
[QUOTE=illusion]Hey,

For example, say I want to access the etc/network/options.txt file.  My probelm is I dont know how to access it through terminal.  Even when I become root through sudo -i or sudo su -, I only have access to the as root user to the root directory.  How to navigate through the other directories?  I'm sure there is a really simple answer, just not seeing it.  
[/QUOTE]

  In terminal:

cd /etc/network
ls

If you want to modify this file:
sudo nano options.txt

instead of nano you may want to use gedit.

Now, I don't know how to use the gui as root. I think this is disable for security reason. Someone may know how to "using nautilus as root".

---

