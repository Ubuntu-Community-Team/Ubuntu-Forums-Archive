---
title: "Installed Ubuntu"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by talon101 on 2008-01-20
Hey guys, 
I'm a very recent convert to the Linux world from xp :) I'm liking what I see in Ubuntu and look forward to using it. I've been a long time user of windows and there are always steps to follow after a clean install (ie firewall, anti-virus, etc). I was wondering if there is anything I need to install/add to my fresh Ubuntu installation such as a firewall. I'm not too worried about virii or trojans and such since its linux :D but what about any security updates, etc.

Also, I'm trying to install an updated nvidia driver. When i go to install it I run into the probably that I have to have root in order to install it. I go to the terminal and switch to root but have no idea on what command to use to run the package. Sorry if this is a noob question for you guys but I have very limited linux experience and looked at the help function but havent found what i've been looking for. Thanks for any help in this matter! ;)

---

### Post by njparton on 2008-01-20
Use envy (google it) to install your nvidia drivers.

Install firestarter to control your firewall if you don't connect to the net via a router.

---

### Post by mikeyphi on 2008-01-20
Welcome!!

Look here for a first guide on the next steps!!
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Security and other updates can be enabled through System/Administration?software Sources
enable the boxes on the Ubuntu software tab and then enable to your choice under the updates tab.

If possible - use the GUI 'Restricted Drivers Manager' to install Nvidia - that way you will get the correct version for your card.

Ask again if there are still/other issues!!

---

### Post by aysiu on 2008-01-20
Read these two links:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Malta paul on 2008-01-20
Hi, a good safe way to update your graph driver is with Envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by talon101 on 2008-01-20
thanks guys

---

### Post by Sef on 2008-01-20
> Also, I'm trying to install an updated nvidia driver.

System > Administration > Restricted Drivers Manager

You will just need to put in your password, and the driver should be installed with no problem.

---

### Post by Ub1476 on 2008-01-20
Hi, welcome to Ubuntu!

As you thought, you won't need anti-virus in Linux. Not really necessary with a firewall either, but it's wise to fire up Firestarter when accessing public/open networks. Ubuntu doesn't really require you to use the terminal, but most guides on the internet use it because it's faster, easier (when you get used to it), and more easy to troubleshoot. For installing ATI and nVidia drivers, there is a nice script called [Envy]("http://albertomilone.com/nvidia_scripts1.html") which will do this for you. Envy can be used in two different ways:

```
envy -g #Graphical interface

envy -t #Text/Terminal interface
```

Say yes when it asks you to configure your X/xorg.conf.

---

### Post by Jelmoh on 2008-01-20
> **Sef said:**
> System > Administration > Restricted Drivers Manager

You will just need to put in your password, and the driver should be installed with no problem.

Is this ATI also? I've got nVidia so it doesn't apply to me.. :P
But I still wonder... :P

---

### Post by Ub1476 on 2008-01-20
It's for every driver which is restricted, which means older ATI (stable) drivers and nVidia drivers. 

It usually doesn't matter whether you use the RDM drivers or the one Envy get for you, but new graphic cards or "rare" might work better with Envy, due to the fact that newer nVidia cards were released after Ubuntu, or they didn't get the time to test them (like the 8800).

For my nVidia 7900 I use the Ubuntu way, but several people I've helped on this forum had needed to use Envy.

---

