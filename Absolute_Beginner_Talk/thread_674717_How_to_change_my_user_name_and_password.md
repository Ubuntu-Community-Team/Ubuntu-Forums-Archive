---
title: "How to change my user name and password"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Boxy1972 on 2008-01-22
Hi i want to give my old computer to my girl friend but she wants a new password and log in i dont want to do a reinstall please can you help thank you .

---

### Post by Xavieran on 2008-01-22
Go to System>Administration>Users and Groups 
and click add user...
that should solve your problems...

---

### Post by PeterJS on 2008-01-22
> **Boxy1972 said:**
> Hi i want to give my old computer to my girl friend but she wants a new password and log in i dont want to do a reinstall please can you help thank you .

You can create a new user in System > Administration > Users and Groups. Create a new account for her, give it a password, enable the account, and add it to the appropriate groups. If you want the new account to behave exactly like the current one copy/move the contents of your home directory (including the hidden directories and files, those contain the settings and stuff)in to the new accounts, and chown the file's to the new account.

---

### Post by prixxie on 2008-03-08
Hello;

I am running Hardy Heron 8.04 from live CD.  Keeps asking for live session password to authenticate and to access hard drive.  The user name is Ubuntu.  I am trying to install on windows XP machine that has crashed due to virus ::)).  Please help.  Thank you. 

Debbie

---

### Post by taurus on 2008-03-08
> **prixxie said:**
> Hello;

I am running Hardy Heron 8.04 from live CD.  Keeps asking for live session password to authenticate and to access hard drive.  The user name is Ubuntu.  I am trying to install on windows XP machine that has crashed due to virus ::)).  Please help.  Thank you. 

Debbie

What happens if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/window
sudo mount -t ntfs /dev/sda1 /media/window -o umask=0222
ls -la /media/window
```
_Assuming_ /dev/sda1 is where your windows partition is.

---

