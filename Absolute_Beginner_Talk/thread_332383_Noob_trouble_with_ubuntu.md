---
title: "Noob trouble with ubuntu"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by noobunt2 on 2007-01-05
Hi. Nice place you got here.

Whelp, I took it upon myself to build a computer over winterbreak because I have a new found passion for open source methods...  sooo, I have installed Ubuntu on it and have been a steady fan for the past three hours.  It's really great, BUT I can't seem to get on the internet... sad, I know.  I would appreciate some experienced help.  The particular irony is I've always used Macs, so I've experienced a lot of "firsts" today (both in building and using a PC).  

The problem is that when I open the network settings administrator it says that i have a dialup modem and there is no option for ethernet.  The motherboard (Asus P5L-VM 1394) has an 1gb ethernet port... and no dialup modem.  I wonder if this has anythng to do with drivers... there are some on the ASUS disc that came with the mother board, but they make no sense to me and the readme is even more confusing.  

This is my first system build, and I am amazed that everything has been so smooth thus far... I wonder if I skipped something during initial setup/boot.  I went through the BIOS and couldn't see anything strange, but I left the settings on defult.  

Any ideas how to get ubuntu to recongnize the ethernet port??  HELP!

---

### Post by finer recliner on 2007-01-06
found this page for you: 
[https://wiki.ubuntu.com/Asus_P5LD2-VM?highlight=%28asus%29](https://wiki.ubuntu.com/Asus_P5LD2-VM?highlight=%28asus%29)

make sure he is referring to the same model mobo you have.

---

### Post by jimrz on 2007-01-06
> **noobunt2 said:**
> Hi. Nice place you got here.

Whelp, I took it upon myself to build a computer over winterbreak because I have a new found passion for open source methods...  sooo, I have installed Ubuntu on it and have been a steady fan for the past three hours.  It's really great, BUT I can't seem to get on the internet... sad, I know.  I would appreciate some experienced help.  The particular irony is I've always used Macs, so I've experienced a lot of "firsts" today (both in building and using a PC).  

The problem is that when I open the network settings administrator it says that i have a dialup modem and there is no option for ethernet.  The motherboard (Asus P5L-VM 1394) has an 1gb ethernet port... and no dialup modem.  I wonder if this has anythng to do with drivers... there are some on the ASUS disc that came with the mother board, but they make no sense to me and the readme is even more confusing.  

This is my first system build, and I am amazed that everything has been so smooth thus far... I wonder if I skipped something during initial setup/boot.  I went through the BIOS and couldn't see anything strange, but I left the settings on defult.  

Any ideas how to get ubuntu to recongnize the ethernet port??  HELP!  

which version of ubuntu have you installed? and what ethernet card?

I recently got a new computer with on-board gigabit ethernet and found that it was not recognized by 6.06 dapper (actually not supported by that kernel version). I tried 6.10 edgy and it works "out of the box".

---

### Post by riven0 on 2007-01-06
> **noobunt2 said:**
> The particular irony is I've always used Macs, so I've experienced a lot of "firsts" today (both in building and using a PC).  


I feel for you. Not only new to Linux, but new to the PC world, too. hehe... :) 

Yeah, first check out the link finer recliner posted and tell us if you have problems. Pretty strange, though, I've got an Asus motherboard with a Gigabit ethernet card and I never had problems. Did you test your connection with the LiveCD? Did it work there?

---

### Post by lukemh on 2007-04-10
i have the exact same problem with the exact same mobo and ubuntu 6.10

the instuctions are not clear in that link.

---

### Post by lukemh on 2007-04-10
maybe i will clarify,

i have the same motherboard, successfully installed Ubuntu 6.10 - i really want to get the network adapter installed!!!

i tried my very hardest to follow the instructions in the link by finer recliner, but it is hard for me to get the packages because i don't have internet access on the Ubuntu computer (obviously: because of the network adapter) - not as easy as firing up synaptic package manager.

i tried to download the packages from this (windows) computer and i burnt them to a CD - copied them to my Ubuntu desktop - and tried to install them, but they have so many dependencies i had to keep going back and forth re-burning more and more packages. i have kinda given up getting the packages that way. IS THERE A windows "package downloader" that will get all dependencies?

so it come down to this: i had no problem downloading the e1000 drivers, but i cannot compile them because i cant get the right packages. (i think i have to downgrade packages too)

please help. thanks.

(it may pay to read the instructions linked by finer recliner, to understand what im trying to do.)

---

### Post by josephus on 2007-04-10
I'm looking through the page now, but you probably don't want to follow the instructions exactly because things like the header files are out of date.

before we continue are you positive that you need to compile this driver (just based on the other user's comments)?

---

### Post by josephus on 2007-04-10
ok.  i've been looking a little deeper at your problem.  unfortunately the asus website seems to be down, but from other sources i've found that your motherboard has an attansic ethernet chipset.  This is different from drivers that you are currently trying to compile.

you'll need to download the source from [http://sourceforge.net/projects/atl1/](http://sourceforge.net/projects/atl1/) and compile those drivers.  

from this bug report ([https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77725](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77725)) it looks like the drivers are now included in feisty.  Since Feisty is coming out so soon (beta is out, release candidate is coming thursday, and final release the following thursday) you could jump in with Feisty now and forget about compiling this.

if you want to stick it out with edgy, let me know and I'll try to walk you through this process.

---

### Post by Patrick K on 2007-04-10
Did you check that it is enabled the BIOS?

---

### Post by lukemh on 2007-04-10
> **josephus said:**
> ok.  i've been looking a little deeper at your problem.  unfortunately the asus website seems to be down, but from other sources i've found that your motherboard has an attansic ethernet chipset.  This is different from drivers that you are currently trying to compile.

you'll need to download the source from [http://sourceforge.net/projects/atl1/](http://sourceforge.net/projects/atl1/) and compile those drivers.  

from this bug report ([https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77725](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77725)) it looks like the drivers are now included in feisty.  Since Feisty is coming out so soon (beta is out, release candidate is coming thursday, and final release the following thursday) you could jump in with Feisty now and forget about compiling this.

if you want to stick it out with edgy, let me know and I'll try to walk you through this process.

THankyou for your research... i was wondering why the windows drivers for my network adapter were from another manufacturer than those e1000 drivers (the ntel look-alikes) :)

**my desicion**: im currently downloading feisty - i feel better about that... 

one question - when the Feisty final comes out i can easily upgrade out of beta yeah?

thanks for your offer to walk me through it, i love the nice caring atmosphere here on ubuntu forums... i may yet take you up on it, if the beta doesnt work, and i need to compile drivers.

thanks again all... i'll report back soon.

---

### Post by lukemh on 2007-04-11
a really big :-D when i put in the ubuntu 7.04 beta live cd and my routers little green "ethernet" activity light came on.... firefox launched, and all systems go. g:):):):):):)gle.com

installing 7.04 beta fixed my problem.

thanks...

oh... also... will my system auto update to 7.04 final when its released?

---

### Post by HereInOz on 2007-04-11
Yes, no worries there.  The changes that are applied to the beta to make it the official release should all be available to you as updates.

---

### Post by arron on 2007-04-11
Hrmmm haven't seen anyone say this yet....  Welcome to the Ubuntu Community!  Im glad that you could get yourself up and running.

---

### Post by josephus on 2007-04-11
lukemh, glad that you got your system working.

---

