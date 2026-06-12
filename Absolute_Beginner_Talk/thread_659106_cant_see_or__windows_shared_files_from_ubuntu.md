---
title: "cant see or  windows shared files from ubuntu"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by samroaf on 2008-01-05
hi 

i cant see windows shared folders and i cant get access to windows network to see if there is a shared folders OR nO each time i try to click on windows network icon
nothing happen dose not shows the page or anything however i can get access to all shared folders and files from windows to Ubuntu but not from Ubuntu to windows and for more inforamtion i allowed from windows file sharing and printing and i turned  firewall  off 

i have the same work group on both machines
i set the shared definition as writable and brows able
by following this guide 
[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

and when i press right click on windows network it says 

[[IMG]http://img69.imageshack.us/img69/4126/screenshot1zr6.th.png[/IMG]](http://img69.imageshack.us/my.php?image=screenshot1zr6.png)

and one MORE MAKE SAMBA START AUTO

---

### Post by mjmurf on 2008-01-05
I'm not sure what the problem is but following the video in this link helped me get mine up and running.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by samroaf on 2008-01-05
> **mjmurf said:**
> I'm not sure what the problem is but following the video in this link helped me get mine up and running.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

thank you for your answer but i already done that i cant see my work group and cant access windows network to see if there is workgroup its like windows network has no access 




any help from anyone i'll be thankful

---

### Post by samroaf on 2008-01-05
is there any one can help

---

### Post by bigken on 2008-01-05
quick and simple 

sudo apt-get install samba
sudo smbpasswd -e <yourname>
sudo smbpasswd -a <yourname>

in windows just run the network wizard in my network places

---

### Post by samroaf on 2008-01-05
> **bigken said:**
> quick and simple 

sudo apt-get install samba
sudo smbpasswd -e <yourname>
sudo smbpasswd -a <yourname>

in windows just run the network wizard in my network places

thank you for ur reply but as i said i can see ubuntu files but i cant see windows shared files

already installed samba and configure it not one time but 5 times 

ok q: how to allow samba startup automatically when system startup

---

### Post by bigken on 2008-01-05
it should start automatically

have shared any folders/files in windows ? also what version of windows

---

### Post by samroaf on 2008-01-05
> **bigken said:**
> it should start automatically

have shared any folders/files in windows ? also what version of windows

yes i have shared files and folders i use xp 

windows network icon should open at least it doesn't do anything

---

### Post by bigken on 2008-01-06
its your windows firewall

---

### Post by samroaf on 2008-01-07
> **bigken said:**
> its your windows firewall

you maybe right if and only if a didn't tured my windows firewall off and i don't have firewall on ubuntu

---

### Post by bigken on 2008-01-08
do you have any other firewalls running ie symantec (norton) or mcafee ?

---

