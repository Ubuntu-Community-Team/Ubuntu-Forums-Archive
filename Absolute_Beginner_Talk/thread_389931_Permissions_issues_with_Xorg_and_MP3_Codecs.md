---
title: "Permissions issues with Xorg and MP3 Codecs"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by DonFunBuBai on 2007-03-21
> **aysiu said:**
> Sounds as if you lost control over parts of your home directory. Type this command into the terminal (substituting in your actual username for *username*) and see if it makes a difference: ```
sudo chown -R *username:username* /home/*username*
```

Hi:
     I'm totally new to ubuntu, and I'm also struggling with the permission stuff. I'm trying to update my Ati driver and try to install some software; however, I kept on encountering a situation where I can't move on.

example 1: For the ati driver update, I first have to modify (adding lines) in the xorg.conf. But it won't let me. I can open xorg.conf with no problem, but after adding lines, I don't see save as an option but save as. So I chose save as and leave everything the way it is, then a message pops up saying "could not save the file."

example 2:
I downloaded the mp3 codec and was trying to make it work. I follow the online instruction step by step. for example, one of the instruction asks me to move the .so file into certain folder. When I'm doing it, a message pops up saying you don't have the permission.

I searched through the forum trying to find ways to solve this yet can't
is there anyway that I can be the superuser the whole time.
how do I chown and tranform root to myself?

Thanks very much for your time

---

### Post by ppatalano on 2007-03-21
In the terminal when you are trying to access the xorg.conf file you have to add sudo before anything to login as root so you will be able to save what you want to edit in the file
Example

```
sudo gedit /etc/X11/xorg.conf
```

It will then prompt you for your root password. Type it in and your set

---

### Post by aysiu on 2007-03-21
ppatalano, for graphical applications, *gksudo* is preferable to *sudo* for [these reasons](http://www.psychocats.net/ubuntu/graphicalsudo).

DonFunFuBai, this page will help you understand how to modify system files (including Xorg):
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

This page will help you understand about software installation:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And this page will help you get MP3 codecs installed:
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

