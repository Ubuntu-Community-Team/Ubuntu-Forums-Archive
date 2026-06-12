---
title: "modify files owned by root"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Keenster on 2006-07-02
Hey guys, thanks in advance for your help.  This is my first ever install of linux and I'm trying to set up a LAMP server to run a webpage off of.

So far ive installed the LAMP version and the GUI, i think its called xubuntu.

Im trying to edit my FTP files but I cant save it in the text editor.  I read in the forums that you can type something like "sudo gedit /ect/vsftpd.conf" but it says "gedit: command not found"  Any idea about what im doing wrong?  Is there away that i can just edit them as root using the GUI?

My other question is im trying to edit the files locally also by using a shared folder.  My server name is "ubuntuserver".  When I run //ubuntuserver in windows i get the login and password screen.  When i put in my initial user (Lets say bob) and password it comes back with
User name:UBUNTUSERVER\bob and nothing happens.  Do i have to put something before the "\bob"?

Sorry for the two questions and thanks again! :D

---

### Post by mlind on 2006-07-02
gedit is a graphical editor that's installed by default on Ubuntu..
You can use nano too, or any other editor.

```

sudo nano /etc/vsftpd.conf

```

You must use sudo to gain root privileges.

---

### Post by aysiu on 2006-07-02
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Keenster on 2006-07-02
thanks, i guess gedit didnt come installed on my system.  I used "sudo apt-get install gedit" and got it going, now I can edit my files.

Anyone know how to fix my network login problem?

Thanks again.

---

