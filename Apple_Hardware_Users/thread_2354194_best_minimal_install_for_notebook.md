---
title: "best minimal install for notebook?"
date: 2017-02-28
forum: Apple Hardware Users
---

### Post by jeff666 on 2017-02-28
So currently I'm running Ubuntu server 16.0.4 lts x86 64bit (natively) on my Mac book. I think using server version might be a mistake (wrong kernel tunning and modules) it runs very hot with just a little stress (like watching a movie). Is there a light weight version of Ubuntu for notebooks that might be less performance tunned  better for battery life? Would i be better off just using Debian standard version (i only ask about another Distro on here because Debian is Ubuntu's parent and a Ubuntu user is a technically a Debian user).ps  I am trying to avoid having lots of programs and GUI per installed so something like Lubuntu isn't exactly what im looking for. thanks in  advance.

---

### Post by ajgreeny on 2017-02-28
I'm not sure from what you wrote if you do or do not want a GUI, but if I understood you properly I think you want a GUI that is usable but not lots of applications that you may not need nor use.

If that assumption is correct install the [Minimum install CD version]("https://help.ubuntu.com/community/Installation/MinimalCD") and then add whatever GUI or DE you want such as lxde, xfce4, openbox, etc, etc, but not one of the ***ubuntu-desktop** packages that also bring in all the default applications of Ubuntu, Xubuntu, Kubuntu, or whichever version you chose.

---

### Post by sudodus on 2017-03-01
Other alternatives include

- start by installing Ubuntu Server (only the basic stuff, no server package, no desktop package).

- boot into the installed (text-screen) system

- install lubuntu-core or xubuntu-core

```
sudo apt-get install lubuntu-core
```
or
```
sudo apt-get install xubuntu-core
```

or even lighter: only a window manager

```
sudo apt-get install fluxbox xinit xterm
```

and after that install the application program packages that you want.

---

### Post by jeff666 on 2017-03-01
@sudodos your suggestions are basically what i already have set up and not really relevant. Sorry im a very poor communicator lol!  What i want to know is are there any differences between server.iso and desktop.iso in the way the kernel is configured?I'm thinking the the kernel for a server.iso might be more performance orientated and desktop.ios more laptop friendly? Thanks.
ps there are different options when building a Linux kernel (in case you didn't know that).

---

### Post by sudodus on 2017-03-01
There is a special low-latency kernel, that you can select for Ubuntu Studio, but I think Ubuntu Server and Ubuntu Desktop share the same kernel (but with separate 32-bit and 64-bit versions).

Right now I use this Xenial kernel (16.04.1 LTS),

```
4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
``` 

and it seems to be the same when installed via the Ubuntu Server iso file and via an Ubuntu Desktop iso file.

But you can still set up things differently, for example the swappiness, in order to get different performance.

The current stable Debian version, Jessie, is based on another kernel series, 3.16. Please try it in order to check if it works better with your hardware. (My experience is that some tasks are more difficult to set up in Debian compared to Ubuntu, but most things work 'out of the box' without tweaking.)

-o-

Setting up ultra light graphics like this

```
sudo apt-get install fluxbox xinit xterm
```

makes a big difference compared to using standard Ubuntu or some other desktop environment with a lot of 'bells and whistles', which means a lot of processes running and adding work-load to the processors.

---

### Post by jeff666 on 2017-03-03
thanks i didn't think just to download the other iso and just check the md5!

I am currently using openbox Cario-dock gnome-terminal xorg which im  very happy with so far (not that flux box doesn't seam like its worth a  try, and im also going to write a script to see how much memory, processor cario-dock and xcompmgr are using see if there is better options out there any suggestions? I really only use dock at coffee shop/ libaray any way, i like to blend in by making my mac look more like a mac other wise people tend not mind their business and ask "how did you do that? blah blah" right click is very effective and clean for me at home.

To bad i don't think swappiness on a Samsung 850 evo 250gb(wish it was a pro 850 nsa proof lol) will make a great difference but maybe a little i will turn it down, the default is 60 so ill try 15. My hard ram is decent amount 3.6 gB and im using a old mac originally 2 x 1gB ram sticks so im assuming Osx had swap which might mean the mother board was better designed for it (Im just speculating). (reading back would i better off with less hard ram, more swap and swapiness at like 40?

any other kernel variables i should change that will help battery? any answer is super appreciated im having a hard time finding info about those. thanks a ton!

---

### Post by sudodus on 2017-03-03
Let us hope some Mac users will see this thread and reply. Maybe chances are better, if a moderator moves the thread to the forum 

[Apple Hardware Users](https://ubuntuforums.org/forumdisplay.php?f=328)

or I think even better if you describe your problem and ask your question in a ***new thread*** with a good descriptive title in that forum.

---

### Post by Bucky Ball on 2017-03-03
Install the 16.04 LTS mini.iso, on first boot issue:

```
sudo apt-get install xubuntu-core^
```

... (don't forget the caret) and you will have Xubuntu-core 16.04 LTS. There's an xfce4 desktop and not much more. You install the apps you want/need, and that includes browser, package manager, etc ...

You can do the same for Lubuntu-core I believe, just change the command accordingly.

---

### Post by slickymaster on 2017-03-03
*Thread moved to **Apple Hardware Users**.*

---

