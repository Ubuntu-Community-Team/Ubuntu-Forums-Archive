---
title: "Gaining root access..."
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Linkiboy on 2006-07-31
Ok.. I'm really really frustrated by now. I'm trying to figure out how to get root access. It's not working. I just installed it, and this darn thing won't let me boot my Windows XP, even though theres an option.

I'm trying to get root because I need to uninstall the old ndiswrapper. I tried typing su and then entering my password, but I got authenication failure. The user I'm on is the only user, the one that was made default by the installer. I don't know what to do, I feel like I've tried everything. Please help...

---

### Post by verbatim210 on 2006-07-31
by default su is locked, cannot use it.

sudo "command" 

will execute a command as the super user

---

### Post by T700 on 2006-07-31
See the "Where's Root" link in my sig for more details.

Paul

---

### Post by benplaut on 2006-07-31
to sum it up, every time a tutorial says su, just type in:

sudo -s
and then your password

---

### Post by gils0040 on 2006-08-01
or you can type:
sudo passwd
set a password and then gain root by issuing su like any other distro

---

### Post by aysiu on 2006-08-01
> **gils0040 said:**
> or you can type:
sudo passwd
set a password and then gain root by issuing su like any other distro
Ah, but ```
sudo -s
``` will achieve the same effect without creating another password.

---

### Post by gils0040 on 2006-08-01
> **aysiu said:**
> Ah, but ```
sudo -s
``` will achieve the same effect without creating another password.

i just used the same password for root as i did for my user account (i know its not the best security). maybe im just lazy but su is easier to type than sudo -s.

---

