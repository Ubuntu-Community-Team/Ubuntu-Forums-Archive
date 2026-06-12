---
title: "can't log into samba share"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by usugar on 2006-10-14
Hi,

I want to be able to browse my home directory from a windows machine.  I have installed samba, shared my home directory, and enabled browsing (all from the System-Administration-Shared Folders dialogue).  The XP machine sees the linux machine but won't accept my username and password (I'm using the same ones as I do to log on to the linux machine). 

What am I doing wrong?  Have I missed a step?

thanks

---

### Post by Kateikyoushi on 2006-10-14
Did you modify the /etc/samba/user file ?
That stores the password.

Read this complete samba installation  [guide]("https://help.ubuntu.com/community/SettingUpSamba").

---

### Post by usugar on 2006-10-15
> **Kateikyoushi said:**
> Did you modify the /etc/samba/user file ?
That stores the password.

Read this complete samba installation  [guide]("https://help.ubuntu.com/community/SettingUpSamba").

Hmmm... was kind of hoping I wouldn't have to start editing files to get something as straightforward as this working :???: .  But thanks anyway - I'll try this when I have some spare time.

---

### Post by docshawnc on 2006-10-15
Go to the terminal and enter
sudo smbpasswd -a your username

---

### Post by usugar on 2006-10-15
> **docshawnc said:**
> Go to the terminal and enter
sudo smbpasswd -a your username

Thanks docshawnc - that worked a treat! :D

---

