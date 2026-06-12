---
title: "N00b needz a li'l help"
date: 2005-05-12
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-05-12
Hey guys, I'm going to go ahead and welcome the mocking that will ensue from asking these very simple questions, but I hope to get to the point where I won't have to ask such simple stuff soon.

Two things, I'm wanting to learn to use apt-get and I want to use Xmms. Can someone give me an idea of how to use apt-get (I've seen it done before when a friend helped me get some packages, and all I remember is him using apt-cache search [data] to find packages) and specifically to get Xmms?

Second, I've tried, unsuccessfully, to mount and unmount a windows partition. I edited fstab and thought I did the syntax correctly, but I'm getting the "no permission to view this folder" error when I try to view the mounted partition. Furthermore, it won't let me unmount the partition to try again. Any help would be greatly appreciated.

---

### Post by vassalle on 2005-05-12
[QUOTE=TheAnonymousx]Hey guys, I'm going to go ahead and welcome the mocking that will ensue from asking these very simple questions, but I hope to get to the point where I won't have to ask such simple stuff soon.

Two things, I'm wanting to learn to use apt-get and I want to use Xmms. Can someone give me an idea of how to use apt-get (I've seen it done before when a friend helped me get some packages, and all I remember is him using apt-cache search [data] to find packages) and specifically to get Xmms?

Second, I've tried, unsuccessfully, to mount and unmount a windows partition. I edited fstab and thought I did the syntax correctly, but I'm getting the "no permission to view this folder" error when I try to view the mounted partition. Furthermore, it won't let me unmount the partition to try again. Any help would be greatly appreciated.[/QUOTE]
 hi, i just picked up linux like 2 months ago, and im still very much a newbie. Theres this website that is very clear in explaining almost everything u'll need to know to get a working ubuntu desktop.. give it a try.. 

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by TheAnonymousx on 2005-05-12
Okay, install Xmms was stupidly easy (and I feel dumbtarded for asking). I still need an assist with the mounting thing though.


Thanks for the webbie suggestion. Checking it out now.

---

### Post by bored2k on 2005-05-12
1) APT
apt-get install application
To install any application [or xmms]

apt-cache search application
To search

sudo apt-get update
To update your database

sudo apt-get upgrade
(Mostly) Harmless upgrade

sudo apt-get dist-upgrade
"Bigger" upgrade

You can open [in your panel] System > Admin > Synaptic and do this the easy way.

2) Mount Windows
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

Read that. Good luck

And by the way no one's allowed to make fun of you or anyother person.

**P.S.** - XMMS is old news, install beep-media-player. Also, from a command line you can type 
man application and you will get a manual for it .

---

