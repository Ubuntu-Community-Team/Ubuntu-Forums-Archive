---
title: "amarok and k3b on ubuntu"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by buntolith on 2006-09-22
Hi,

I have tried both ubuntu and kubuntu and I think I prefer ubuntu. But I also prefer amarok as my mp3 player and k3b to burn cd/dvd and to convert dvd to avi. Does amarok and k3b work just fine under ubuntu/gnome? If it does, why does it say it is only for kubuntu?

Is there any software that can only run on gnome and vice versa or can you run just about any software on both versions (ubuntu/kubuntu)?

Thanks...

---

### Post by JAwuku on 2006-09-22
As Ubuntu and kubuntu are both on the same repositories, it should be OK to install KDE apps on Gnome and vice-versa.

You can use **aptitude** instead of apt-get to install and uninstall, as this uninstalls all dependencies.

For example, to install k3b

```
sudo aptitude update
sudo aptitude install k3b
```

and to uninstall k3b completely, use

```
sudo aptitude remove k3b
```

to get you back to the original state.

---

### Post by buntolith on 2006-09-22
Ok, thanks.

I'll try your suggestion...

---

### Post by Drakkor on 2006-09-22
Yep, I use K3b,and Amarok on Ubuntu/Gnome and they work just fine ! :D

---

### Post by Brunellus on 2006-09-22
they will work, but not be as pretty as they are in KDE.  That's about it.

---

### Post by redpants on 2006-09-22
I had amarok installed, then upgraded to 1.4.0, but I wanted MTP support for my Zen, so I tried later upgrading to 1.4.3 (I think they added MTP at 1.4.2) but I kept getting errors saying that 1.4.3 had dependencies that were not installable (the exact message is Depends: libvisual-0.4-0(>=0.4.0) but is not installable).  I looked around and I read some forum posts that said that amarok depended on libraries from KDE and could not run properly on Gnome, so I just gave up on amarok.  But then I read this thread... so would the "aptitude" command fix my problem?  If yes, what would the code be to install the latest version of amarok (1.4.3)?

---

### Post by konst88 on 2006-09-22
i have amarok 1.4.3 which runs perfectly under gnome.
i installed it from the repository given on it's home page.
[http://amarok.kde.org/](http://amarok.kde.org/)

---

### Post by redpants on 2006-09-22
Weird.  I followed the directions on their page and that's when I got the errors.  I noticed in my synaptics manager that Amarok states that it needs libvisual OR XMMS installed...I just remembered that I used to have XMMS installed but uninstalled it because I never used it...so I wonder if that's why I can't upgrade Amarok...maybe for Gnome it needs XMMS?  Total guessing on my part, but I'm just trying to figure out what the deal is.  I'm going to try reinstalling XMMS when I get home (I'm at work and can't connect my laptop to the internet here to download the needed install files).

---

### Post by Drakkor on 2006-09-22
Any major improvements ? I have 1.4.2 and don't want to mess it up,lol :p

---

### Post by konst88 on 2006-09-23
no idea about XMMS.. i never had it installed...

---

