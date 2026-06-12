---
title: "How to Install Apps???"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Robroy11976 on 2005-11-17
Hi, newbie here ... just installed ubuntu, it's my first time .... i was trying to play an mp3 file ... but it says that i have to install a plugin to make it run.  So i downloaded lame mp3 encoder/decoder as well as divx 5.  But the problem is i don't know how to install it ... need help???  I tried running the install.sh file (just like the way you do with windows), but to no avail ... I only succeded in installing the flash plugin for firebox, as it has only an instruction to run a file in the terminal window.

---

### Post by discofro on 2005-11-17
Almost everything in linux requires a terminal command to install it. Check the file extension of the packaged you downloaded, i.e. tar.gz, .deb, etc and run a search on  the command lines for those. Some of them are pretty simple, especially .deb's

For instance, in the terminal just type sudo dpkg -i package.deb, and replace 'package' with the name of your file. 

It just takes a little practice.

---

### Post by etc on 2005-11-17
You should take a look at [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") or [EasyUbuntu]("http://ubuntuforums.org/showthread.php?t=64629"), which will install your mp3 codecs and other things for you.
But if you want to install other things, you should use apt-get or it's GUI frontend Synaptic Package Manager, which both have heavy documentation if you look in the wiki.

---

### Post by Robroy11976 on 2005-11-17
ic ... i'll try out the .deb you suggested ... how about if it's tar.gz???  Btw, is the automatix or easyubuntu is for ubuntu only??? or for the whole linux OS based in general???

---

### Post by Kvark on 2005-11-17
Almost all programs are installed with Synaptic Package Manager that you can find in the menu. You will love Synaptic when you realize how easy it is to find and install programs with it ;)

But that doesn't help in this case with something you found and downloaded the old fashioned way... There are almost always instructions on how to install it included in .tar.gz downloads. Is there any text file called install or readme there that has any instructions?

---

### Post by Robroy11976 on 2005-11-17
Yes, but i can't seem to understand it's intructions ... kinda like i'm lost in the linux world :)

---

### Post by Kyral on 2005-11-17
Tar.gz, the old fashioned way, and sometimes very fun. Basically you extract it

```
tar -zxvf <nameoffile>
```

Configure (after changing into the directory the Tarball made)

```
./configure
```

Compile...

```
make
```

and install!

```
sudo make install
```

Of course it rarely goes off without a hitch. Dependacy hell and all. I smell another edition of Terminal For Beginners (I'm stuck monitoring the computer labs for 3 hours tomorrow after class, what else am I gonna do?!)

---

### Post by aysiu on 2005-11-17
Please read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

It explains all the major ways to install software in Ubuntu--from easy to not as easy.
I suggest you take the easy route first--Synaptic Package Manager (totally graphical, point-and-click) or apt-get (the terminal version), as you can get MP3 encoding that way (you do not need a separate .tar.gz or .deb or .rpm.

---

### Post by Robroy11976 on 2005-11-18
Thanks guys ... i'll do some crack course now :)

---

