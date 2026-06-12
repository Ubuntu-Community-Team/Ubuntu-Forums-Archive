---
title: "sudo denied"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by DamagePlan on 2008-01-26
richard@Dyson:~$ root
bash: root: command not found
richard@Dyson:~$ su -
Password: 
su: Authentication failure
Sorry.
richard@Dyson:~$ 


What am I doing wrong here?

---

### Post by emrahustun on 2008-01-26
that's **sudo**.
and you must use sudo with a command.
type sudo and you can see these commands.

---

### Post by stevescripts on 2008-01-26
sudo -i  ? looks (to me) like what you might be looking for

Steve

---

### Post by nikoPSK on 2008-01-26
for ubuntu if you want root login you do sudo su or sudo -i :)

---

### Post by DamagePlan on 2008-01-26
Thanks for replies.

Yeah I tried sudo but it doesnt work.

richard@Dyson:~$ sudo /etc/X11/xorg.conf
sudo: /etc/X11/xorg.conf: command not found
richard@Dyson:~$

---

### Post by nikoPSK on 2008-01-26
if you want to edit it do this:

sudo gedit /etc/X11/xorg.conf

but why do you want to edit it?

---

### Post by PmDematagoda on 2008-01-26
You should use sudo with a proper command, meaning it appends a normal command such as:-
```
gedit /etc/X11/xorg.conf
```
which you cannot use to edit xorg.conf, to:-
```
**sudo** gedit /etc/X11/xorg.conf
```

You cannot use sudo as stand-alone, you need to use it with a proper and working command.

---

### Post by mister_pink on 2008-01-26
You have to tell it what you want to do - sudo just gives you root priviledges, and xorg.conf is just a text file. I think what you want is 
gksudo gedit /etc/X11/xorg.conf

I've used gksudo there because its a graphical application.

Edit: That was some impressive simultaneous giving of the same answer...

---

### Post by DamagePlan on 2008-01-26
Thanks for replies.

I wish to try and edit xconf because I cant go over a certain resolution. I need 1440 * 900.

---

### Post by nikoPSK on 2008-01-26
> **DamagePlan said:**
> Thanks for replies.

I wish to try and edit xconf because I cant go over a certain resolution. I need 1440 * 900.

ah, understood. :)

---

### Post by aysiu on 2008-01-26
If you do not even have a graphical environment to work in, you can also try using the Nano text editor instead of Gedit: ```
sudo nano -B /etc/X11/xorg.conf
``` This translates to mean *Since I am administrator of this computer, temporarily allow me to use the Nano text editor with root access for this one task of editing the xorg.conf, which lives in the /etc/X11 directory while simultaneously making a backup copy of the file before I edit it.*

---

### Post by mmichalik on 2008-01-26
Great advice!  Backup everything before you edit. 

I got cocky once about 10 years ago and deleted an entire MS-SQL production database by accident.  Thankfully, I had just made a backup of it and was able to restore it before anyone came in that morning.......

---

### Post by Mr.popo on 2008-01-26
Thankyou!
Im now clear aswell

---

