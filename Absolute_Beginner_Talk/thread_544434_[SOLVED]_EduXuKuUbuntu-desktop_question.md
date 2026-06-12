---
title: "[SOLVED] Edu/Xu/Ku/Ubuntu-desktop question"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by WebSiteGuru on 2007-09-06
Good morning everyone,

Got a quick question!

I  had installed Ubuntu on my computer with Gnome Desktop. I had been happy using it. :D


From reading all these forums about installing other desktop environment using
```
sudo aptitude install Edu/Ku/Xu/Ubuntu-desktop
```


Last night, I had decided to try it out and I love it.

My question is:

Since I had installed Ubuntu first, can I remove it using

```
sudo aptitude remove ubuntu-desktop
```


Or, will it cause any problem?

---

### Post by mocoloco on 2007-09-06
Hey Guru, fancy seeing you again here :).  The answer is unfortunately, no.  Those packages are what we call "meta-packages", and they basically have all the corresponding desktop software listed as a dependency.  So when apt is told to get that package it sees that it must first install all the dependencies.  Turns out the meta-package itself installs nothing, it's just there to make it easy to get all the others without having to select them one-by-one.
However when removing the meta-package the dependencies are not removed.
Here's what you need.
[http://psychocats.net/ubuntu/purexfce]("http://psychocats.net/ubuntu/purexfce")
By the way that site has some great info.

---

### Post by WebSiteGuru on 2007-09-06
> **mocoloco said:**
> Hey Guru, fancy seeing you again here :). 

LMAOL! Nice to see you again too :lolflag: As I mentioned (some where in one of the thread, I think)  ;) I am here to stay and learn, and asking a **lot** of questions is how I learn. And fancy me, you are the first to answer my question. :D


> **mocoloco said:**
> The answer is unfortunately, no.  Those packages are what we call "meta-packages", and they basically have all the corresponding desktop software listed as a dependency.  So when apt is told to get that package it sees that it must first install all the dependencies.  Turns out the meta-package itself installs nothing, it's just there to make it easy to get all the others without having to select them one-by-one.
However when removing the meta-package the dependencies are not removed.


:( Oh well Guess I have to leave it that way. ;)


> **mocoloco said:**
> Here's what you need.
[http://psychocats.net/ubuntu/purexfce]("http://psychocats.net/ubuntu/purexfce")
By the way that site has some great info.

I heard so much about this site, I have not had a chance to really sit down and visit it yet (since I can not access the site from work :(). But I will from home. :)

---

### Post by WebSiteGuru on 2007-09-06
Anyway, thanks for the info. :D

---

### Post by deadgobby on 2007-09-06
Well GSU,
 That is supper that you got the GUI running.  You are doing good and now you want to see other desktops. The above post did lead the right way. You can ask the question what is best. By Asking that question is going to bring lot this and that is best. All the desktops are good and it is up to you what you like. So enjoy all the flavors of freedom of linux. That my friend is the best thing of the O/S. You can choose, play with it, mold it any way, shape it, and form it to your liking. Welcome to what is left of the free world of linux.

---

### Post by mocoloco on 2007-09-06
Well put deadgobby.  I prefer Gnome, but I like all three flavors of Ubuntu, and have them on different machines (I don't like to mix them, I know it doesn't hurt anything but I don't like seeing all the KDE apps in my Gnome menu.  I'm a bit picky, I know).  They're all fun to use and for someone who likes tinkering on computers it's tons of fun to learn the ins and outs of different desktop environments.

---

### Post by WebSiteGuru on 2007-09-06
> **deadgobby said:**
> Well GSU,
 That is supper that you got the GUI running.  You are doing good and now you want to see other desktops. The above post did lead the right way. You can ask the question what is best. By Asking that question is going to bring lot this and that is best. All the desktops are good and it is up to you what you like. So enjoy all the flavors of freedom of linux. That my friend is the best thing of the O/S. You can choose, play with it, mold it any way, shape it, and form it to your liking. 

Thanks! Questions will be ask for sure, dont worry about that. I still have a lot more questions, but it will be as I go.

I am just testing on the different looks and feel of the different desktops. And trying to find out what I like best. ENJOY, I will! :D

> **deadgobby said:**
> Welcome to what is left of the free world of linux.

My dear deadgobby, it is not "what is left of the free world of linux". it's the begining of the FREE world of Linux! ;)

---

### Post by WebSiteGuru on 2007-09-06
> **mocoloco said:**
> Well put deadgobby.  I prefer Gnome, but I like all three flavors of Ubuntu, and have them on different machines (I don't like to mix them, I know it doesn't hurt anything but I don't like seeing all the KDE apps in my Gnome menu.  I'm a bit picky, I know).  They're all fun to use and for someone who likes tinkering on computers it's tons of fun to learn the ins and outs of different desktop environments.

Everyone do have their preference. I am in the way feel the same way. But since I only have 1 computer to deal with ATM, that will do. :D

---

