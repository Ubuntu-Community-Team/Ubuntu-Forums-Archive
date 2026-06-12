---
title: "desktop effects not running!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by mattigus on 2007-04-29
Hey

I've just recently got Ubuntu to work, after a great amount of effort.  In the process, I had to install fglrx drivers to get the video to work.  Now I'm trying to turn on desktop effects and I get this error:

"The Composite extension is not available"

What do I do to get desktop effects up and running?

---

### Post by viciouslime on 2007-04-29
> **mattigus said:**
> Hey

I've just recently got Ubuntu to work, after a great amount of effort.  In the process, I had to install fglrx drivers to get the video to work.  Now I'm trying to turn on desktop effects and I get this error:

"The Composite extension is not available"

What do I do to get desktop effects up and running?

Unfortunately, you can't. Desktop effects don't work with ATI cards if you use the proprietary driver. After sending an e-mail to ATI telling them how important it is that they start supporting linux properly, you might like to try XGL. See the ubuntu wiki and other posts in here for guides.

---

### Post by freebird54 on 2007-04-29
You may have to switch to running Beryl on XGL to get it to go.  fglrx does not work on AIGLX, which is necessary for the 'normal' desktop effects to work.  there are lots of Howtos around here on 'Xgl with beryl' - though I am not sure I know if they have any differences with Feisty.  Here's one i used to get going in Edgy.  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

Hope it helps...

---

### Post by viciouslime on 2007-04-29
> **freebird54 said:**
> You may have to switch to running Beryl on XGL to get it to go.  fglrx does not work on AIGLX, which is necessary for the 'normal' desktop effects to work.  there are lots of Howtos around here on 'Xgl with beryl' - though I am not sure I know if they have any differences with Feisty...[/url]

Hope it helps...

Indeed they do. Here it is: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by mattigus on 2007-04-29
Ive been following that wiki, and I'm having problems already.  the "deb" command is not recognized when i try to use it, and when i try putting the files in through the windows manager, it says I dont have permission.

---

### Post by zetsumei on 2007-04-29
Are you doing everything with sudo in front of the command?  And the deb..... goes into your sources.list file.  Once there just follow the tutorial.

---

### Post by Hackza on 2007-04-29
Um permissions... I presume your getting 

[PHP]bash: deb: command not found[/PHP]

I'm very new to linux and all that goes with it but try looking in synaptic package manager (system -> administration) for it?

EDIT: [https://answers.launchpad.net/ubuntu/+question/1514](https://answers.launchpad.net/ubuntu/+question/1514)    (top result on google)

---

### Post by IronicLogic on 2008-01-07
Hi, I have a question about how to get Compiz running on my system. It is an Acer Power 2000 system, Core 2 Duo 2GHz, 1 GB RAM, on board 128 MB video RAM, 946 Intel chipset. I would have thought this would have been adequate to run Desktop Effects but I get a message saying that my PC can't run any of the effects (for Gutsy)! I had to wipe the hard drive clean and do a fresh install as the original machine was Japanese. Are there any drivers that are required to get the system to run Compiz? Any help would be great.

---

