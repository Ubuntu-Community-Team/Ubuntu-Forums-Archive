---
title: "PLEASE Make my Ubuntu experience better!"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by The Weather Underground on 2007-05-10
Alright, it's Day 1 of Ubuntu, and I've been messing around with it for a full day. I've managed to re-direct my user directory to the root directory assuming it would make things easier, while on the contrary it locked me out of Ubuntu, which caused me to reboot. So then I was trying to hook up my internet on Ubuntu (I'm on a laptop right now), and while in the command I typed in lshw, which apparently is a big no no, and causes your ubuntu to completely crash, not even allowing you to restart. I have hope for this operating system, I really do. I love the freedom of it, and how freakin convienent it is. I'm just waiting on Zune support, and I will just be complete.

But for now, I have other problems.

1. Earlier, I tried to dual boot, but every time the computer would boot up it would bypass the linux partition all together, and go straight to XP. SO, I tried just formatting the whole hard-drive, and installing it that way. Well, it hasn't exactly gone over to well, and every time I started up the computer, I had to boot it from the ubuntu disk, and then I could start it from the hard-drive. It would always come up "Error, no operating system detected" without the disc! What could this be? Should I partition it in an NTFS or Fat32?

2. Wireless internet. I have a WRT54GX2 router, with a SX400 adapter on my computer, and it won't connect to the internet. Now, I've read up on it, and it said that if it wasn't supported you have to sort of figure it out yourself through other people or guides. So, I did what it also reccomended and downloaded ndiswrapper. The intall text that came with it was pretty foreign to me, and I looked to the troubleshooting in the Wiki, and it was pretty confusing as well. So, some help on that would be excellent. I just don't really know where to go with ndiswrapper, so if someone could give me a tip on that, it would be excellent. 

Once I get past these two things, I will be dandy like candy. Thanks for any help given beforehand!

---

### Post by bobplano on 2007-05-10
1. for dual-booting always install windows first as it takes over your hard drive. the partition should be in ntfs. then install ubuntu. you can choose whatever option you want, but one of them wipes your hard drive and installs only ubuntu on there. the partitons for ubuntu should be /(root) ext3, about 10-20 gigs if you can give that much room, otherwise 5-6 should be good for regular use. /home is your personal files. it can be as big as you want. also ext3. then swap, double your ram, or 512mb-2 gigs. this should be in swap format but you can choose ext3 then when you mount it changes it. 
2. ndiswrapper can be gotten a few ways. since you are on a laptop you can just plug in and go to synaptic and look for ndiswrapper. you'll need ndiswrapper-utils and ndiswrapper-common. if your card reuires a newer version you will need to compile it, but that isn't as hard as you think

---

### Post by The Weather Underground on 2007-05-10
Thanks a lot!

---

### Post by Danielinux on 2007-05-10
hello, i think this guide will help you a lot with the most common things.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

read it carefully.

see ya later:lolflag:

---

### Post by The Weather Underground on 2007-05-11
whenever I type in 

sudo apt-get install ndiswrapper

I get 
Reading package lists...Done
Building Dependency Tree...
Reading state information...Done
E: Couldn't find package ndiswrapper

The ndiswrapper folder is saved to the desktop...do I have to specify where that is?

---

### Post by bobplano on 2007-05-11
apt-get installs it from the repos. you just need to click on it to run it. it's easier plus i forgot the terminal command. maybe i'ts something like```
cd Desktop
./ndiswrapper-common
```
do you have the .deb files or the .tar.gz file?

---

### Post by The Weather Underground on 2007-05-11
tar.gz

---

### Post by bobplano on 2007-05-11
you'll need to extract it first. if you are plugged in so you can get the internet copy+paste into the terminal:
```
sudo aptitude install gcc cpp build-essential linux-headers-$(uname -r)
```
otherwise get the package buil-essential and all its dependencies from [www.packages.ubuntu.coim](www.packages.ubuntu.coim) and install those. then go to the extracted directory (ndiswrapper) and run
```
sudo make
sudo make install
```
this will set up ndiswrapper and then run
```
 sudo ndiswrapper -i *path/to/driver*
```

---

### Post by The Weather Underground on 2007-05-11
You guys are so much help thank you so much!

---

### Post by The Weather Underground on 2007-05-13
Alright, I never was able to get the internet working. I tried the commands in the Terminal, and I got ndiswrapper installed, but the driver on my WRT54GX2 .inf file just will not be read by ndiswrapper! when I do this command

 sudo ndiswrapper -i path/to/driver

nothing happens. I have the right path and everything, nothing happens at all though.

---

### Post by bobplano on 2007-05-13
the path/to/driver is replaced by whatever the actual path is. just making sure. is it started? do 
```
sudo ndiswrapper -m
```
also try this
```
sudo modprobe ndiswrapper
```

---

