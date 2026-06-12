---
title: "Changing from Kubuntu to Ubuntu?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-05-09
I run Ubuntu on my old laptop and so far am very happy with it. I then decided that I would try Kubuntu on my desktop thinking that it would be very similar. Unfortunately I am unable to "get on" with Kubuntu and would now like to install Ubuntu in it's place. Is this a straightforward instal over procedure or will I have to delete the Kubuntu partition. 
I am a relative newbie to Linux and would be grateful for any help.

---

### Post by Seisen on 2007-05-09
How did you install Kubuntu?

---

### Post by Benbow on 2007-05-09
I downloaded it from the website and installed it to my hard drive.

---

### Post by n0dl on 2007-05-09
Well from reading your post i presume that you just want to use the ubuntu desktop instead of KDE. Simply 
```
sudo apt-get install ubuntu-desktop
```
Then youll have gnome, all the gnome apps, and stuff.

---

### Post by Inxsible on 2007-05-09
you can do 
```

sudo apt-get install ubuntu-desktop

```
 
This won't remove Kubuntu from your machine but give you the opportunity to either use the Gnome desktop or the KDE desktop.
 
Another way is to completely overwrite the KDE environment and install the Gnome. Do this if you are sure that you dont want KDE at all, so that you dont have the KDE clutter- so to speak

---

### Post by Nythain on 2007-05-09
pop in your ubuntu disk, and during install process instead of deleting all the partitions and starting over, you could just format them...

if you didnt want to go that route, you could
sudo aptitude install ubuntu-desktop
sudo aptitude --purge remove kubuntu-desktop
should hopfully do the trick

---

### Post by ajmannen on 2007-05-09
Or you could simply delete the linux partition with Gparted and then install a fresh ubuntu 7.04 on the empty partition

---

### Post by Benbow on 2007-05-09
Ahhh! little problem, I omitted to say that the version of Ubuntu is Ubuntu Ultimate which is the same as the basic but with about 1gb of extras and it is this which I want to use??

---

### Post by Seisen on 2007-05-09
Follow this guide

[http://www.psychocats.net/ubuntu/gnome]("http://www.psychocats.net/ubuntu/gnome") then to remove KDE follow this guide
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by Inxsible on 2007-05-09
> **Benbow said:**
> Ahhh! little problem, I omitted to say that the version of Ubuntu is Ubuntu Ultimate which is the same as the basic but with about 1gb of extras and it is this which I want to use??
 
In that case, you will probably have the CD for it. Correct?
 
Just put it in, and re-install over the same partitions where you installed Kubuntu. You won't have to create any more partitions. Just check the boxes to format them to EXT3 and use them as your / (root) and /home partitions, or however you have your partitions created currently.

---

### Post by Benbow on 2007-05-09
Thanks all. Sounds good to me, two alternatives there to try, I will start with installing via my old DVD.
Thanks again

---

### Post by Benbow on 2007-05-09
Thanks all, will try the install from original dvd first and go from there.
Thanks again

---

