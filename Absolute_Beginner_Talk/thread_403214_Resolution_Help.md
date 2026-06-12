---
title: "Resolution Help"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by falonyn on 2007-04-06
My laptop is a 15.4" widescreen Gateway MX6960 with _Intel GMA 950_ and is currently running Dapper Drake. I am thinking abou upgrading to Edgy Eft today. It supports 1280 x 800 resolution.

Okay, s I wasn't able to get this problem fixed yesterday and I have been searching for something that might work. So far I haven't found anything that promising other than the xorg file (I tried this and it completely messed up my system. I am sure I did something wrong, but I am fairly new to Ubuntu and so I don't know what to do when selecting through all of those options.)

The other way was linked to me by Roger. [http://ubuntuforums.org/showthread.php?t=351647]("http://ubuntuforums.org/showthread.php?t=351647")

My problem with this second method was on the very first step. I am to open synaptic and add extra repositories. I went through the synaptic but couldn't find what I thought I was supposed to be looking for, and in reality, I don't know what I am looking to add. 

If anyone on here could help walk me through either process I would greatly appreciate it. This is so far the only problem with Ubuntu I am having, but it is a frustrating one to have. 

Also, should I upgrade and then fix this problem? Or should I fix it and then upgrade?

---

### Post by x64Jimbo on 2007-04-06
Just open up your /etc/apt/sources.list and uncomment all the universe and multiverse repos.

---

### Post by falonyn on 2007-04-06
> **x64Jimbo said:**
> Just open up your /etc/apt/sources.list and uncomment all the universe and multiverse repos.

Is that something reached through the synaptic or do I have to use the command line? If I have to use the terminal, what comman to I use?

Very noob to this whole thing. Thanks

---

### Post by spinflick on 2007-04-06
Enable the extra repositories in Synaptic. press the reload and close.  

Open up a terminal and type.... sudo 915resolution -l 

and check your readings with the readings from the other thread and change what needs to be changed.

---

### Post by falonyn on 2007-04-06
> **spinflick said:**
> Enable the extra repositories in Synaptic. press the reload and close.  

Open up a terminal and type.... sudo 915resolution -l 

and check your readings with the readings from the other thread and change what needs to be changed.

Thank you. I finally figured it all out. And now that I have the resolution set it looks so much better. My only question now is will this work if I upgrade?

---

### Post by spinflick on 2007-04-07
Yes it should keep your settings when you upgrade to Feisty, unless you do a fresh install. The upgrade you want to be aware of is the kernel upgrade, I think half the forum lost x after the last one but was soon put right. :)

---

