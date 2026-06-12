---
title: "Flash Player"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2007-05-22
Need basic, specific steps to install Flash to view videos on sites such as Youtube.com  I am new to ubuntu and new to using terminal, need easy, basic steps to install.  thanks

---

### Post by Kobalt on 2007-05-22
Applications > Accessories > Terminal
After this enter : ```
sudo apt-get install flashplugin-nonfree
```
Restart your browser, you're done :)

---

### Post by bvexen2 on 2007-05-22
this is the message I got when I tried...

mcbride@74-128-67-134:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by Kobalt on 2007-05-22
Which version  of Ubuntu are you runing ?

---

### Post by bvexen2 on 2007-05-22
not sure, how do I find out?

---

### Post by Kobalt on 2007-05-22
You should find something under System > Admin. > System monitor.

---

### Post by bvexen2 on 2007-05-22
ubuntu 5.10

does that help?

old version?

---

### Post by Kobalt on 2007-05-22
I'ts quite old yes...
Anyway if you want to flash plugin, check [it]("http://psychocats.net/ubuntu/flash#adobe") out

---

### Post by dr.silly on 2007-05-22
were on 7.04 now that was 1.94 versions ago, quite old

sudo apt-get dist-upgrade

warning this will take a few hours depends on internet connection

---

### Post by JuggaloZeke on 2007-05-23
> **Kobalt said:**
> Applications > Accessories > Terminal
After this enter : ```
sudo apt-get install flashplugin-nonfree
```
Restart your browser, you're done :)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate


Didn't work. :( I'm a Ubuntu/Linux newb, too, and I tried getting Flash directly from Adobe but I have no idea how to install this .tar.gz file. I just don't know how to do this step:

4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

How do you "navigate" in the terminal.

---

### Post by dr.silly on 2007-05-23
it means go to the directory where you downloaded

say you put it in a folder on your desktop called flashplayer

```
cd /home/*(insert your username here)*/Desktop/flashplayer
```

now the terminal is 'in' that folder which means all it's links and things are relative to that folder
now type in whatever it told you to and it will install

---

### Post by apunc1 on 2007-05-23
[QUOTE=J

4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

How do you "navigate" in the terminal.[/QUOTE]

```
cd
```

=change directory

so if you downloaded the installer to your desktop you would enter
```
cd ~/Desktop
```

and then enter the command to run the installer

---

### Post by JuggaloZeke on 2007-05-25
Ok, thanks for that information. :) Now, where can I get a flash installer for x86 64 architecture? :(

---

### Post by aysiu on 2007-05-25
> **JuggaloZeke said:**
> Ok, thanks for that information. :) Now, where can I get a flash installer for x86 64 architecture? :(
Try [this](http://ubuntuforums.org/showthread.php?t=202537).

---

