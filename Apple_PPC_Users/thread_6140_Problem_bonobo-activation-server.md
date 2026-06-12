---
title: "Problem bonobo-activation-server"
date: 2004-11-25
forum: Apple PPC Users
---

### Post by parrish on 2004-11-25
Hi 
I have PB-333Mhz.

and when I make upgrade of the system they appear the problems with bonobo-activation-server and I cannot do nothing this is the problem anybody has the solution

thank

parrish

---

### Post by SyL on 2004-11-25
I had the same pb after a brutal reboot. I just installed all bonobo package with apt-get and that worked.
 What is the error message ?

---

### Post by parrish on 2004-11-25
it says:  that it cannot activate the applet and it suggests to deactivate the bonobo-activation-server.  This happens single when I update distro

sorry my english is so so

parrish

---

### Post by SyL on 2004-11-25
I don't really understand the pb.
  Check if the bonobo configuration path is ok :
  ```
bonobo-activation-sysconf --display-directories
```
  
  if is empty do this :
  ```
bonobo-activation-sysconf --add-directory=/your/path
```
  seek the bonobo file *.server. Normally is here : /usr/lib/bonobo/servers
 
 
 If that not work yet, try to seek into all bonobo file and bin, there is a lot of options.
  
  Hope that will help you

---

### Post by Jad on 2005-03-09
What is bonobo activation server ?

---

### Post by SyL on 2005-03-14
[QUOTE=Jad]What is bonobo activation server ?[/QUOTE]
 I'm not sure but I think that bonoboo activation server manage the clock of gnome. If the system crach because the battery is empty on the next reboot, if the laptop is not connect to internet for check the exact time, that's explose and a lot of gnome composants don't work.


Someone would be able to tell us more ??

---

### Post by khc on 2005-03-15
bonobo is the GNOME component framework based on COBRA, similar to KParts in KDE. bonobo activation server is a component in the framework, and that's all I can tell you since I am not too familiar with bonobo myself. I believe all applets are managed by it though.

---

### Post by lorenzo on 2006-03-15
After a failed attempt to suspend my laptop I have this "bonobo activation" problem too.
I made the suggested checks and modification but, some here and then the problem occurs again. 

I have to kill the bonobo activation process and everything works correctly until the next boot (or one of the next reboots).

Not a blocking error but quite an annoying one. Any hint?

Lorenzo

P.S.
I use breezy i386, reiserFS fileSistem

---

### Post by indypende on 2006-03-17
Hi all,
i have a pb g4 whit dapper perfectly working but every time i reboot or start my pc without the ethernet cable i can't access the gnome session and i receive the "bonobo-activation-server crash" that stop nautilus and the gnome-panel!!!
No possibilities of resolution until i reboot wired?? IT'S SO SADLY!
please help me...
HI!!!
mik

---

### Post by dieza on 2006-07-07
What I did, ctr+alt+F1
sudo pico /etc/network/interfaces
#edit my network preferences to my new location
cd /etc/init.d/
./networking restart
# to check if something "ping www.google.com" with success 
reboot
# and voilà my Powerbook is running UBUNTU again

---

### Post by ianare on 2007-11-21
> **lorenzo said:**
> 
I have to kill the bonobo activation process and everything works correctly until the next boot (or one of the next reboots).
Not a blocking error but quite an annoying one. Any hint?

Lorenzo

this is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/libbonobo/+bug/90923](https://bugs.launchpad.net/ubuntu/+source/libbonobo/+bug/90923)

---

### Post by SyL on 2007-11-30
> **ianare said:**
> this is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/libbonobo/+bug/90923](https://bugs.launchpad.net/ubuntu/+source/libbonobo/+bug/90923)


Bug #90923, first reported on 2007-03-09
Post creation: November 25th, 2004 

it took almost 3 years to get it reported!

---

