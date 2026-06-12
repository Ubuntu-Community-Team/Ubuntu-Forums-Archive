---
title: "Compiling a Kernel with the newer version of Ndiswrapper"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by aberry5555 on 2007-06-11
Ok, this is a little long-winded but I, personally, cannot see any other way around my problem. I've just installed Feisty Fawn and so far, so good. Alot of the problems such as dodgy ATI GFX detection and such have been solved and everything auto-installed bar one thing; my wifi. 

I'm running Feisty on an Asus A8V-E Deluxe Mobo which has a marvel libertas wifi chip, which I eventually got working in Edgy using Ndiswrapper. When I first tried it I installed Ndiswrapper using Synaptic, but I had problems as it was (and seemingly still is) an out of date package; you could use a network-driven app for a few seconds and then the whole PC, including the mouse, would freeze and required a hard-shutdown. So to get around it I removed it in Synaptic and manually compiled the latest version, which worked absolutely perfectly, not one single glitch. The major problem with this was that every time I updated the kernel I had to reinstall ndiswrapper, which required me moving my PC back to the router and using a patch lead to use the net. 

The last time I needed a kernel upgrade I decided just to scrap it and install Feisty. Alot of stuff has been improved including one good idea; including Ndiswrapper in to the kernel itself. This is great as it means that, if it worked, I wouldn't have to keep reinstalling Ndiswrapper every time I updated the kernel. However since it's the older version of Ndiswrapper (out of date by around about a year it seems) I can't use it, and I don't think I can remove it to install from source either.

So my question is this, can anyone think of any other way of installing Ndiswrapper without building my own kernel and, if not, is anyone willing to explain how to, basically, compile an exact copy of the current kernel either minus Ndiswrapper or with the newer version of it?

Thanks in advance, I hope!!

---

### Post by Seisen on 2007-06-11
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

There are direction to follow to compile the kernel. Just don't do the changes and you will have the same settigns as your current kernel.

---

### Post by aberry5555 on 2007-06-11
do you know how not to include ndiswrapper?

---

### Post by aberry5555 on 2007-06-11
Can anyone from the Ubuntu development team tell me whether you're planning to upgrade the included ndiswrapper package in a kernel upgrade anytime soon? If so I'll wait till then as I tried to compile my own kernel and all that happened was I broke synaptic :S

---

### Post by Bachstelze on 2007-06-11
I don't think the ndiswrapper shipped with the Ubuntu kernel will be upgraded until Gutsy is out.

However, it's very easy to compile the newest ndiswrapper without needing to rebuild the whole kernel.

First, install the tools needed for compiling :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then grab the source for ndiswrapper and copy it to your Desktop in Ubuntu and do

```
mkdir ~/ndiswrapper
cd ~/ndiswrapper
mv ../Desktop/ndiswrapper-1.46.tar.gz .
tar xzvf ndiswrapper-1.46.tar.gz
cd ndiswrapper-1.46
sudo make uninstall
```

Run the last one as many times as needed until you see nothing under that line :


```
Run uninstall as many times as necessary until no "removing" messages appear below.
```

then, run

```
make
sudo make install
```

Voilà :) you have the latest ndiswrapper.

---

### Post by aberry5555 on 2007-06-12
Thank you!! I'm going to try that after a fresh install tonight, you're a life-saver, for a few days I thought I wasn't gonna be able to use Feisty :S Once again Ubuntu forums and its wonderful users save the day, hehe

---

