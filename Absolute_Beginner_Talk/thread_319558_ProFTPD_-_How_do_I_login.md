---
title: "ProFTPD - How do I login?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by esf8 on 2006-12-15
Hi!

I followed this guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server)

It installed fine, I made all the changes...

Now how do I login?! :D How do I create additional users for the ftp server?

Why doesn't the guide explain this?

Thanks!

---

### Post by wieman01 on 2006-12-16
There is a nice tool called "gproftpd" which you'll find in the repositories. It's basically a GUI for "proftp" and makes administratives tasks like creating users, etc. much more convenient. Give it a go!

---

### Post by esf8 on 2006-12-16
I apologize wieman01, I should have mentioned that I was running Ubuntu Server and that a GUI isn't an option. :neutral:

---

### Post by esf8 on 2006-12-17
Surely someone here uses ProFTPd...

---

### Post by jms1989 on 2006-12-20
> **esf8 said:**
> Surely someone here uses ProFTPd...

I use it, but I'm in the same position. I don't know how to setup the users and the gproftpd doesn't do what it's supposed to do. I'm trying to use webmin to set it up but no success. The server starts but can't login, I need it for my php scripts.

---

### Post by esf8 on 2006-12-21
So nobody here who uses ProFTPD has any idea how to set it up? Even the official documentation doesn't describe it correctly (either that, or I'm not reading it correctly)

---

### Post by Bachstelze on 2006-12-21
I personnally use vsFTPd but I think I can answer. FTP is just another way to login on the system, just like SSH or physical login. So just add normal users, like this

```
sudo useradd -m username
```

remove the -m if you do not want to create a home directoy for the user.

---

### Post by esf8 on 2006-12-22
> **HymnToLife said:**
> I personnally use vsFTPd but I think I can answer. FTP is just another way to login on the system, just like SSH or physical login. So just add normal users, like this

```
sudo useradd -m username
```

remove the -m if you do not want to create a home directoy for the user.

Thanks a lot for the reply. I tried this, but when I login it gives me "incorrect password" even though the user is correct and I literally just SET the password.

I'm using the default config file + the changes noted on the Ubuntuguide guide.

---

### Post by esf8 on 2006-12-26
I'm not gonna start complaining about how an official guide does not work when one follows the instructions perfectly, or how "this is the type of response you get from a 'friendly' linux community", but I'm really wondering here:

does ANYONE use proftpd? or am i better off using something else? ](*,)

---

### Post by esf8 on 2006-12-31
Suggestions? This is ridiculous! ](*,)

I don't want to install X11 to configure a ftpd

---

### Post by wieman01 on 2006-12-31
Have you seen [this]("http://www.ubuntuforums.org/showthread.php?t=79588")? Talks about user administration as well.

---

### Post by houstonbofh on 2006-12-31
Not sure how I missed this one the last few days bit I did.  You might have had better luck posting it in the server forum.  Anyway, it uses the Linux users and home directories.  The config file in /etc can be used to set up anon access, or chroot home directories.  Mostly, however, it just uses the settings you have for the Linux system.

---

