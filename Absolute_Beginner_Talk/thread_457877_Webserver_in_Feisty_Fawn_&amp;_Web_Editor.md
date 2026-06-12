---
title: "Webserver in Feisty Fawn &amp; Web Editor"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Pathan on 2007-05-29
Hi,
I am a newbie to Ubuntu. Few days back, I installed Feisty Fawn. I want to install a webserver to test my web projects locally. Kindly guide me to setup a webserver on my Fesity Fawn. Do I need a internet connection to access something like repositries for this installation?
I use[ Programmers Notepad]("http://www.pnotepad.org/") to edit my web pages and other stuff. Is there any alternative for it in Linux? My overall expression is **"UBUNTU ROCKS".**

---

### Post by Eagle 101 on 2007-05-29
Not sure about the webserver stuff, but there are a ton of text editors in linux. Lets see...

1. kate
2. vim
3. emacs
4. mousepad
5. a ton more!

---

### Post by justleen on 2007-05-29
installing a webserver doesnt require a internetconnection, as far as i know the packages are on the live cd
```
 sudo apt-get install apache2 
```
that is enough to install it. afterwards, you can browse to [http://localhost](http://localhost) to test it

---

### Post by Pathan on 2007-05-29
Thanks mates for help. @Justleen: Will this install mysql support too?
@Eagle 101: I used all of these editors over Redhat Linux. I want like on i mentioned. I am 99% sure there will be some alternative for it in Linux. Thanks all.

---

### Post by esoterica on 2007-05-29
Sounds like your doing exactly what I'm after, user name HymToLife around here I've found to be the Apache expert and usualy jumps on these posts, seems to be gone when I need her help the most tonight though.

I have the LAMP installed on my Ubuntu 7.04 Desktop, it all works as expected, now I'm just trying to fine tune it, I still have some issues that the documentation I followed didn't properly cover, but it does get you at least up and running.

You can search my own past posts and follow a good learn from someone else mistakes for you to use.

This documentation will get you up and running Apache, PHP, MySQL...

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It gets you going, though I do think the documentation needs some cleaning up and fine tuning to be as good as other Ubuntu documentation I've so far found, up and working is good though,m it will get you there. Too much reference to "choose any method" for installing rather than just telling you the best suggested method would be a great improvement.

If you search my posts here you'll find where I used "aptitude install" to get there, however now that I do have it working and I've learned more I wish I would have instead just followed these instructions...

[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

In fact as of now, I'm seriously rethinking about removing what I currently have working by following the Ubuntu documentation and instead following the instructions they have here at Security Focus.

As far as editors go, the best your going to find for this is gedit, we have another post going right now where username mcducks mentioned there are plug ins available for gedit, again search my user name and you'll find this info.

---

### Post by Pathan on 2007-05-29
Thanks fellows for help.

---

