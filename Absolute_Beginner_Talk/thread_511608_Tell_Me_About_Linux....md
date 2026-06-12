---
title: "Tell Me About Linux..."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-28
Name All Linux Programs! Im Downloading Every Linux Os And Seeing Which On Is The Best! Give Me A List Of Every One Please. I Only Know Of - Ubuntu - Xubuntu - Kubuntu - Puppy - Dsl

---

### Post by tomcheng76 on 2007-07-28
you mean Linux distributions?
see here [http://distrowatch.com/](http://distrowatch.com/)
i bet you cannot dl them all :)

---

### Post by WarholsGhost on 2007-07-28
have fun

[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

---

### Post by 4Real on 2007-07-28
well i have 100 pack of CD-R's.... I have great internet speed..... I have lots of time... Yes I WILL DO IT!

---

### Post by 4Real on 2007-07-28
DAMN over 1,00 of distros! Amazing...  Windows doesn't have that do they?

---

### Post by tomcheng76 on 2007-07-28
just try those popular one in distrowatch
many of them have LiveCD, great :D
but i sure that Ubuntu is one of the most popular and user friendly distributions as i stick with it LOL

---

### Post by 4Real on 2007-07-28
K cool... Where can i get Ubuntu media codecs? It wont play music and has no sound...

---

### Post by 4Real on 2007-07-28
Is This How You Do It? - 

If you need to play mp3 files and have some of the codecs that dont come with Ubuntu you need the w32codecs.

This file is not available through Synaptic Package Manager so you will need to get it online and install it by double clicking it once its on your desktop.

*Update! You need to get the extra repositories enabled on the Synaptic Package Manager and paste these codes in the terminal:

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \

gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \

gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

---

### Post by tomcheng76 on 2007-07-28
yeah , just a little sudo aptitude install command helps
the only problem is the ensure you have the repositories

basically this is enough
```

####
# Edgy
####

deb http://jp.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://jp.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://jp.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe

```

---

### Post by 4Real on 2007-07-28
hello anyone? no help? :(

---

### Post by 4Real on 2007-07-28
> **tomcheng76 said:**
> yeah , just a little sudo aptitude install command helps
the only problem is the ensure you have the repositories

basically this is enough
```

####
# Edgy
####

deb http://jp.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://jp.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://jp.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe

```

so the a web link , i go to the site and get repositories? bit confused... but yeah im new to linux... im only 13! :P

---

### Post by meborc on 2007-07-28
read this - [www.ubuntuguide.org](www.ubuntuguide.org) to get everything working... a great guide to ubuntu

---

### Post by 4Real on 2007-07-28
ok thanks for the link

---

### Post by Vague on 2007-07-28
> **4Real said:**
> ok thanks for the link

Also, don't forget about [the wiki](http://wiki.ubuntu.com) and the [help pages](http://help.ubuntu.com).  They can be pretty helpful.

---

### Post by 4Real on 2007-07-28
oh yeah wikipedia is good thanks all. I bookmark all my threads so i can look back at them.

---

### Post by BobCFC on 2007-07-28
If you click on search at the top of the forums you will see that you can pick **Find all your posts** and **Find all your threads** from the bottom of the list.  You can also click on someones name to find all posts by that person or send them a private message.


If you want to play an mp3 or divx just double click on one and the player will ask you to click Yes to search for the codecs automatically.


If you want to add extra repositories click on System->Admin->Software Sources and then use the 3rd party tab.

---

