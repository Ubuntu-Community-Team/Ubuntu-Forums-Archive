---
title: "Add/Remove Applications cannot connect to Internet"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by kstella on 2007-05-02
First off, I'm new to Ubuntu and just recently installed Feisty Fawn as part of a dual-boot (because my school still uses some Windows-only compatible programs).

Anyway, I wanted to enable my system to play mp3s, etc. and found everything I needed in [this sticky post]("http://ubuntuforums.org/showthread.php?t=413624"). However, when I tried to install the plugins using Add/Remove Applications, the connection timed out. It also failed to find the nearest mirror for downloads.

My computer gets Internet access through LAN; in particular, Firefox connects thanks to an automatic proxy configuration script. But are there any settings I need to change so that I can add more applications?

Thanks.

---

### Post by kstella on 2007-05-02
Just an update:

While reading about related problems on this forum, I was able to reconfigure some settings. Add/Remove Applications now connects to the Internet, but now it can't download repository indexes. Someone had a similar post, so I'll wait and see if it gets resolved. :)

---

### Post by zvacet on 2007-05-03
I don´t know how to solve your problem,but I can tell you to make your setting as they were before you change it.It is important to have synaptic and apt-get or aptitude working then add/remove.You can download everything you need with synaptic or apt-get or aptitude.

---

### Post by kstella on 2007-05-03
I'm not sure if I understand your post. Um, as far as I know, synaptic package manager is working; according to synaptic, what I'm looking for is already installed. But it won't work in Add/Remove.

---

### Post by kstella on 2007-05-03
This has been resolved. :)

---

### Post by Sef on 2007-05-03
Could you please post how it has been resolved?

---

### Post by trebian on 2008-03-10
in my pc apt is not working too.
only the firefox can access the internet. before I disable the ipv6 firefox could not connect too.
pidgin, add/remove and apt has no connection.
in add/remove the error message is :"Click on 'Reload' to load it. To reload the list you need a working internet connection. "
I don't know what to do??! 
help me!

---

### Post by Sweetsupremacy on 2008-04-09
I would love to know how the problem was resolved... I've got the same issue as above.

---

### Post by patrickaupperle on 2008-04-09
> **trebian said:**
> in my pc apt is not working too.
only the firefox can access the internet. before I disable the ipv6 firefox could not connect too.
pidgin, add/remove and apt has no connection.
in add/remove the error message is :"Click on 'Reload' to load it. To reload the list you need a working internet connection. "
I don't know what to do??! 
help me!

Try going to the terminal and typing
```
sudo apt-get update
```

Type your pass.

Try add/remove again.

Edit: In case you don't know, Terminal is in applications, accessories, terminal

---

