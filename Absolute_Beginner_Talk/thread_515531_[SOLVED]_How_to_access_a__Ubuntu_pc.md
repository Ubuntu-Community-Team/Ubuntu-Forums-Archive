---
title: "[SOLVED] How to access a  Ubuntu pc ?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by befana on 2007-08-02
Hi!
I have two pcs at home - one with Windows XP and the other with XP and Ubuntu 7.04, and they are connected in lan. But when the dual-boot mashine is under Ubuntu I can not access it from the xp computer - it asks me for a user name and password. I use my ubuntu's username and password to access it, but ubuntu don't let me to get on it. Please, help!

P.S Sorry about my bad english :(

---

### Post by scxtt on 2007-08-02
how are you trying to connect to it from XP - using samba (network neighborhood)?

---

### Post by befana on 2007-08-02
Yes, I think using Samba. The XP computer recognizes the other pc like a samba server.

---

### Post by scxtt on 2007-08-02
on your ubuntu pc, enter the following into a terminal:

sudo smbpasswd -a $USER

where $USER is your username in XP ... enter the password when prompted, use your XP password for that ... if you do that, it'll be much more "automatic" ...

---

### Post by befana on 2007-08-02
But I don't have a XP password. Do I have to make one?

---

### Post by scxtt on 2007-08-02
not sure that you "have to" but it's my understanding that when XP tries to authenticate via samba to your ubuntu box, it'll use your XP user's password by default ... at worst, you may be prompted for the password you entered when you ran smbpasswd ...

---

### Post by ugm6hr on 2007-08-02
> **befana said:**
> But I don't have a XP password. Do I have to make one?

If you want to access Ubuntu shared files without a password - look at this:
[http://ubuntuforums.org/showpost.php?p=3113048&postcount=2](http://ubuntuforums.org/showpost.php?p=3113048&postcount=2)

---

### Post by befana on 2007-08-03
My Samba server was not properly configured. I've read this:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
and I've made it.
Now it's O.K.

Thanks for your help!

---

