---
title: "How Can I Use KDE on XUbundu"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by vibinkgl on 2007-01-16
Hi All,

I am Using an Old PC(P3 800 Mhz , 128 MB RAM). I already install XUbundu and it's work well.
i would like to Install KDE on it. Is't Possible ?

If possible, please tell me how , and from where can i download KDE.

Thanks in Advance

---

### Post by NeoLithium on 2007-01-16
```

sudo aptitude install kubuntu-desktop

```
Should work; that way if you don't like it, it's easy to remove, for a lighter version, I think you can use kde-core in place of kubuntu-desktop; as well.

---

### Post by Sef on 2007-01-16
It's possible, but it likely will not work well.   Kubuntu and Ubuntu both really need 128 mb ram to work well.

---

### Post by 3rdalbum on 2007-01-16
It's both possible and easy, but I don't know how well it will run (if at all) with 128 megabytes of RAM.

How much hard disk space do you have available? If you've got 3 gigabytes or more free, and you want all the programs that Kubuntu comes with:

sudo aptitude install kubuntu-desktop

Otherwise, if you don't have a lot of space left or you just want the desktop:

sudo aptitude install kde-core

or for a little more functionality:

sudo aptitude install kde-base

When you've installed KDE, you can switch to it by going to the Options menu on the login screen, selecting the Sessions menu item and choosing KDE. Login, and you will get to KDE.

---

### Post by vibinkgl on 2007-01-16
Hi all,

I am very new to Ubundu. Anybody tell me from where i can download KDE package ?
I Have KUbundu Live CD. Is't enough  ?

---

### Post by Extreme Coder on 2007-01-16
I'm not sure if this is the way, but that's what I did in the days of the Dapper:
```
sudo apt-cdrom add /media/cdrom0 #or insert the location to your CD-ROM if it is different
sudo aptitude install kubuntu-desktop 
```

Somebody correct me(and slap me in the face) if I'm wrong too.

Extreme Coder

---

