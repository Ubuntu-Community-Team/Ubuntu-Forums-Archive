---
title: "Problems installing nvidia-xconfig"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Perigon on 2006-04-07
So, I downloaded nvidia-xconfig in hopes of installing new nvidia drivers (currently using the Vesa driver as the nvidia driver included with Ubuntu wasn't working for me), but whenever I try ./configure within the extracted folder, it just tells me that no File or Directory exists. I haven't been able to find a solution to this problem, can someone walk me through the process of installing and setting up new Nvidia drivers step-by-step (in Linux-newbie/dummy terms)? ](*,)

---

### Post by aktiwers on 2006-04-07
Hi,

Try this
[http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

And 
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

These both help you install a lot of very useful apps and also the Nvidia drivers.

---

### Post by tseliot on 2006-04-07
OR you can use my guide (it seems long because I've tried to explain things as clearly as possible):

[HOWTO: Latest NVIDIA drivers]("http://ubuntuforums.org/showthread.php?t=75074")

---

### Post by Perigon on 2006-04-07
tseliot, I tried Method 2 from your guide, and after the first command I get the following error:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-.34

```

---

### Post by Mustard on 2006-04-07
[QUOTE=Perigon]tseliot, I tried Method 2 from your guide, and after the first command I get the following error:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-.34

```[/QUOTE]

You made a typo when you entered the command.  Its gcc-3.4, not gcc-.34.  You might be better off copying and pasting the commands into your terminal to avoid making more typing errors.

Attention to detail is an important aspect of using linux.  I'd be interested in what process you went through to install the nvidia drivers from the repositories, as I'm thinking that you may have made a similar error in detail when you tried that method.

---

