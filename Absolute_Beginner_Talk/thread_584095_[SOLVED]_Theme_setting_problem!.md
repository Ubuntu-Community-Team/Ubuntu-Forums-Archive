---
title: "[SOLVED] Theme setting problem!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-10-20
Guys if i set the theme (right click(desktop) > Change Desktop Background) the theme is applied fine. But there seems to be 2 themes, what i mean is for some of the applications specially for administrative apps it shows in one theme and for other apps the theme selected. Sounds confusing :( check the screenshot attached....

the left side pane shows some different theme for root (opened that pane using "gksudo nautils"). The right side pane is the theme i have set.. opened that from Places > Computer. the same applies to many dialog boxes too! specially those which require root password! kindly help.

---

### Post by FuturePilot on 2007-10-20
That's because you're using a theme that you installed. It gets installed into your home folder and then when you run a root app, the themes aren't applied because it's using the root settings. So to fix this, give this a try
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
```

---

### Post by dimbulb1024 on 2007-10-20
Nice FuturePilot.
I always wanted to use my themes for root, but didn't want the hassle of logging into root and then loading them.

---

### Post by Dr Small on 2007-10-20
> **FuturePilot said:**
> That's because you're using a theme that you installed. It gets installed into your home folder and then when you run a root app, the themes aren't applied because it's using the root settings. So to fix this, give this a try
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
```
That is probably an easier way than what I use :p
I normally just login as root under gnome and change the theme :D

But, that will work too.

Dr Small

---

### Post by llamakc on 2007-10-20
Another thanks for the tip.

---

### Post by Frak on 2007-10-20
> **FuturePilot said:**
> That's because you're using a theme that you installed. It gets installed into your home folder and then when you run a root app, the themes aren't applied because it's using the root settings. So to fix this, give this a try
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
```
Leave it to FuturePilot to find a completely easy way to do something while the rest of us do it the hard way ;)

---

### Post by FuturePilot on 2007-10-20
> **Frak said:**
> Leave it to FuturePilot to find a completely easy way to do something while the rest of us do it the hard way ;)

:lolflag:

Lol. I didn't know this many people had this problem.:lolflag:

---

### Post by badguyanil on 2007-10-20
Thanks FuturePilot for the tip...will try this one out... 

Thanks Dr Small too! As far as i know, under ubuntu we do not have a root login as a seperate login i guess... all apps with root preveliges have to be run using "sudo". Is there any way around and login as root!

---

### Post by Dr Small on 2007-10-20
> **badguyanil said:**
> Thanks FuturePilot for the tip...will try this one out... 

Thanks Dr Small too! As far as i know, under ubuntu we do not have a root login as a seperate login i guess... all apps with root preveliges have to be run using "sudo". Is there any way around and login as root!
Yes. I wrote a howto on this here:
[http://php.8ez.com/drsmall/blog/?p=114](http://php.8ez.com/drsmall/blog/?p=114)

---

### Post by Frak on 2007-10-20
> **badguyanil said:**
> Thanks FuturePilot for the tip...will try this one out... 

Thanks Dr Small too! As far as i know, under ubuntu we do not have a root login as a seperate login i guess... all apps with root preveliges have to be run using "sudo". Is there any way around and login as root!
There is, its just not recommended.

---

### Post by badguyanil on 2007-10-20
so how do i login using the root login! Just to know the how to's....what is the user name we use! just "root" i guess. Will give it a try!

---

### Post by Frak on 2007-10-20
> **badguyanil said:**
> so how do i login using the root login! Just to know the how to's....what is the user name we use! just "root" i guess. Will give it a try!
It won't work.

---

### Post by Dr Small on 2007-10-20
> **Frak said:**
> It won't work.
It looks like I caused more problems than good by posting that :|

That howto is only for expirenced users!

Dr Small

---

### Post by llamakc on 2007-10-20
Heh. About 9 years ago when I started messing with Linux I made the fatal rm (-Rf) mistake inside of /etc, then I rebooted. Waahhh!

When I first came to Ubuntu (from Debian) I resented the lack of root user. Now I completely recognize the need for it.

---

### Post by Frak on 2007-10-20
Its bad security practice in the first place to login as root in the first place. i.e. why we have sudo.

---

### Post by badguyanil on 2007-10-21
But still knowing isnt bad i guess... neways sudo does all i need so i am happy with that! But still out of curiosity would still love to know how to be a root!!!

---

### Post by Frak on 2007-10-21
```
sudo su
```
BOOM ROOT! The safe way.

---

### Post by badguyanil on 2007-10-22
Great! Boom Boom!

---

