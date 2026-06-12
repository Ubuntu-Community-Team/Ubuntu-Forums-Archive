---
title: "Just installed Xubuntu; can't download/install any new packages..."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-12
I'm very new to Linux, so forgive any ignorance on my part. When I go to Application > System > Add/remove, And I browse all those neat programs, I can't download any of them for two reasons. 

ONE: It says that almost none of them are compatible with my machine. "[blank] cannot be installed on your machine (i386)" 
TWO: Then, the very few that are allowed on my machine give me the error that the list needs to be reloaded using an internet connection. So I click okay aind it looks like it does something, but gives me the same crap. I know my internet is working because I'm using my Xubuntu laptop to type this right now.

Could these things be because of the Xfce interface? Would using Kubuntu or Ubuntu fix that? Also, this is on an HP laptop, which apparently suck with Gutsy Gibbon; could downgrading to Feisty Fawn fix my problems? I even tried downloading Opera and OpenOffice from their websites and I can't get them to install; though that might be due to my own incompetence.

Please help or give any suggestions at all. I'm very new to Linux and don't want to give up already.

---

### Post by taurus on 2007-12-12
Open a terminal and enable all the repos in your /etc/apt/sources.list if you want to install additional apps.

```
gksudo mousepad /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```
Now, you should be able to install whatever you want from Add/Remove.

---

