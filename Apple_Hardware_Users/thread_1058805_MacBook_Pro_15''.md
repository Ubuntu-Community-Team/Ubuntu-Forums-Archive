---
title: "MacBook Pro 15''"
date: 2009-02-03
forum: Apple Hardware Users
---

### Post by panosher on 2009-02-03
I just ordered the new MacBook Pro 15''. i wanted to ask you , if you experienced any problems with ubuntu 8.10 besides the heat... or if you know any other distro that plays good with it.

Thank you,
Kind Regards Panagioti.

P.S i've read similar threads but i thought it is a good idea to have a thread only about the new MacBook. :)

---

### Post by buntuLo on 2009-02-03
> **panosher said:**
> I just ordered the new MacBook Pro 15''. i wanted to ask you , if you experienced any problems with ubuntu 8.10 besides the heat... or if you know any other distro that plays good with it.
Thank you,
Kind Regards Panagioti.
P.S i've read similar threads but i thought it is a good idea to have a thread only about the new MacBook. :)

hi Panosher, have a look at the documentation page for this specific hardware, it is constantly updated:

[https://help.ubuntu.com/community/MacBookPro5-1/Intrepid](https://help.ubuntu.com/community/MacBookPro5-1/Intrepid)

i got my MacBook Pro 5,1 three weeks ago and i'm very happy running Ubuntu (Kubuntu is my personal choice) on it! good luck, Lo.

---

### Post by panosher on 2009-02-03
Hello, thank you for the reply !

i have seen this page already, but thank you !

You mentioned Kubuntu and i checked it out !

it uses kde and not gnome. I couldnt find a lot of information in the site so can you please inform me about the main differences and why should i install Kubuntu than Ubuntu ?

Also has anyone installed Debian or Centos to MacBook ? And how did it go ?

I use Ubuntu 8.04 to one pc and Centos 5.1 to another.

buntuLo which way did you do the install with the BootCamp or using rEFIt ?

Thank you.

---

### Post by cyberdork33 on 2009-02-03
> **panosher said:**
> it uses kde and not gnome. I couldnt find a lot of information in the site so can you please inform me about the main differences and why should i install Kubuntu than Ubuntu ?
Mainly, it is KDE vs Gnome. It is matter of which you like more.

> **panosher said:**
> Also has anyone installed Debian or Centos to MacBook ? And how did it go ?
There are plenty of people using debian on Macs. Plus, since Ubuntu is based on Debian, in a way, Ubuntu users are running debian on their machines too.


> **panosher said:**
> buntuLo which way did you do the install with the BootCamp or using rEFIt ?
BootCamp and rEFIt are completely different things... I would recommend using BOTH of these tools to install Ubuntu on your Intel Mac. rEFIt is a set of useful tools and a graphical boot menu... Bootcamp is a collection of things, but mainly a GUI to resize your OSX partition for windows and a set of Window Drivers. that is all.

---

### Post by panosher on 2009-02-03
Thank you for your quick reply !!!

So i will go with both ! i was just asking because i read both ways
and i could not decide.

I ll inform you in three days when i have tha mac in my hands how i did it 

Thank you again !

lets see what we can do about the heat prob. As far as i read there is no side effects besides the battery-life and of course the heat. I think at the moment we should be a little careful until we will come over it.

**Linux Rulez, Ubuntu Rulez !**

---

### Post by buntuLo on 2009-02-03
Panosher, Cyberdork answered your questions already and very clearly.
i'd just add that the choice of Gnome/KDE (in my case) is mainly due to the suite of applications and utilities coming with them (e.g. Konqueror and digiKam). once you install Ubuntu/Kubuntu, you can always install (simply as a package) also the second desktop manager and switch between them to test.
about the installation, i did not use Bootcamp, but ran Ubuntu live and used GParted from there to resize. then burned a cd with rEFIt and installed it afterwards.
about Debian on this machine, i found useful informations on the page [http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)
what surprised me there is that many solutions for this new hardware were actually taken from the Ubuntu Forums! these forums are really one of the reasons for me to use (K)Ubuntu :~)
once more, good luck with your coming toy! Lo.

---

### Post by w00t951 on 2009-02-03
Well, another problem with the new aluminum MacBook Pro is the electric shocks that occur evey once in a while (which is to say every ten minutes) and the keyboard layout, along with the lack of device drivers. I mean, the new NVIDIA 9400 card is fine, but the NVIDIA 9600M needs a graphics driver that is compatible with Ubuntu. I had a really hard time with the drivers search, as they would either cough up an error message or just not install at all. I'm still looking for them.

---

### Post by buntuLo on 2009-02-03
> **w00t951 said:**
> Well, another problem with the new aluminum MacBook Pro is the electric shocks that occur evey once in a while (which is to say every ten minutes) and the keyboard layout, along with the lack of device drivers. I mean, the new NVIDIA 9400 card is fine, but the NVIDIA 9600M needs a graphics driver that is compatible with Ubuntu. I had a really hard time with the drivers search, as they would either cough up an error message or just not install at all. I'm still looking for them.

hi w00t951,

i never had any 'electric shock' actually.. what do you mean with it?

indeed keyboard mapping is still troublesome also for me, together with the audio support (one speaker missing).

the Nvidia 9400 M is actually not usable on the MacBook Pro 5.1 (and i want to believe just for now) cause of bios-emulation booting issues.

on the other hand, the Nvidia 9600 M GT works perfectly under Ubuntu8.10 with the proprietary driver nvidia-glx-180 as with the previous 177. you can easily find the 177 in the configuration gui "hardware drivers", while you can install the 180 with
```
sudo apt-get install nvidia-glx-180
```
hope this helps! Lo.

---

### Post by panosher on 2009-02-03
buntuLo thanks for the info.

As ubuntu is a debian project, i ll stay with it cause i like it more.
I was wondering though if the clear Debian version was playing better, but you answered already :)

Again with the partition are too many opinions. So i guess i ll try to find witch method is safer, and i think is with rEFIt.

> Well, another problem with the new aluminum MacBook Pro is the electric shocks that occur evey once in a while (which is to say every ten minutes)

w00t951, it is the first time i hear about that. Is it also confirmed by other users ?

---

### Post by cyberdork33 on 2009-02-03
as far as "electric shocks" are concerned, I think he might be referring to static electricity being conducted through the metal housing. This would be true for any metal object though. Being one that is prone to such things, especially in Winter, I don't really notice it much, but I do get a shock from my MacbookPro4,1 every once in a while when I pick it up (and it is off). But I also get shocked when I touch a car door, building doors, other people, faucets, pretty much anything metallic and it has nothing to do with the computer itself.

---

