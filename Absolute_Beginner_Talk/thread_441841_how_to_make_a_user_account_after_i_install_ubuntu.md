---
title: "how to make a user account after i install ubuntu?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by claymore666 on 2007-05-13
as per the topic, how to make a user account after i install ubuntu? (im using ubuntustudio!)

please be aware that my install did not ask for a password for either root or a user account name/ pass.

---

### Post by bobplano on 2007-05-13
```
sudo adduser *username*
```
if you want the new user to be able to use sudo then add admin to the end of it

---

### Post by claymore666 on 2007-05-13
Thanks, now how do i login root? lol, i didnt even get to set a root password.

---

### Post by claymore666 on 2007-05-13
btw, eys i know, you can't login on root, but i didnt get a chance to enter root/ sudo password on installation and for my user/ account, same story as root on installation

so basically im stuck on ubuntustudio login screen without a username/ password to login to do anything.

---

### Post by seshomaru samma on 2007-05-13
i dont think you can install an ubuntu without giving your user a password
with sudo and your user password you can run as root

---

### Post by stijngysemans on 2007-05-13
> **bobplano said:**
> ```
sudo adduser *username*
```
if you want the new user to be able to use sudo then add admin to the end of it
Or go to system > administration >> user and groups.

---

### Post by zvacet on 2007-05-13
To temporarly become root you can type **sudo** in front of command or
```
sudo -i
```

With this command you become root and after that type commands you need

---

### Post by claymore666 on 2007-05-14
Thanks, what happened is i forgot to add user/ password in the *text based* install of ubuntu studio (and the beta i installed before i accidentally skipped aswell - i think it's a menu pathing bug where it skips it, if you choose not to do something with your network config or something, it's odd.

I re-installed and closely followed the prompts!

if this happens to anyone else, boot into recovery mode and as root, type 'useradd or 'adduser -p -g adm, admin,cdrom,audio,video<<password>> <<username>>

(i think!)

and you _should_ be able to at least login.


Thanks!

---

