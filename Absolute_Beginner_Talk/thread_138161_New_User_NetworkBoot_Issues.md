---
title: "New User Network/Boot Issues"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by sony102600 on 2006-03-01
Hi there, I am completely new to linux and ubuntu, and I am trying to set up a dual boot machine with windows xp and ubunto.  I have been reading for a couple days now, and I seem to be unable to find or understand solutions to the problems that I have.  Here is what I am dealing with so far, in order of importance of needing to be getting fixed.

1.)  Internet Connection Notworking - I have seen this problem before, I am running an onboard nick card from an AsRock Dual 939 motherboard.  The auto dhcp network setup during install failed, and I have tried going into system and activating the eth0 zero device they have mentioned there.  Do I just need to find some linux drivers for my nic card?  

2.)  Screwed Up Booting Sequence - As I said before, I am trying to set up a dual boot machine.  I have one hard drive with ubuntu, one with windows.  When I start up my machine normally, it will go straight to windows.  Now, for to get into ubunto, I need to go into the setup menu from the post screen, and go to ide drives.  It will say no ide slave drive detected(my master drive is a sata 2 drive, that is where windows is).  However, when I press enter on the slave ide driver, it will open up the properties for my actual ubuntu hardrive, and it will say "new hardware detected, please reboot", if I save and exit, the next time my computer boots, it will boot off the ubuntu drive.  Obviously, I would like to set it up so I can just choose from the post screen, or something similar, and I know it has something to do with boot programs being install on both hard drives, but I am unsure as to which boot sequence device I should delete(the windows or ubuntu one), and how I would go about doing so.

3.) Installing Programs, Plugins - I have been unable to install any new programs ( I downloaded a .deb file for the music program amarok, but I guess you just can't double click it to install... :-(  )..  I have reading about respositories, but can't seem to get a handle on them and how they help in installing programs..  Also, my mp3s will not play using the standard ubuntu audio player, and Im guessing there is some plugin availeable to install, but again, am unsure where I would find one and how to go about implementing it.

Thanks for the help in advanced.  I ranked getting my internet to work as the most important, so that way I can spend reading guides and forums without having to leave ubuntu, so any help there would be greatly appreciated!

Tony

---

### Post by Beej on 2006-03-01
Hi i cant help you with 1 or 2 (sorry) but 3 is relatively easy. Amarok is in the repositories these are easy to use (if you have an internet connection). I assume you are using gnome. 

Go to system > administration >  synaptic package manager

click search and type the name of the program you wish to download (amarok in this case) or the type (for example media player) right click on the package you want and click install. then click the apply button at the top. Synaptic will automatically install any other packages needed for you program to work.

Amarok is an excellent choice by the way!

Alternatively this can be done from the terminal. 

Go to applications > accessories > terminal

at the prompt type "sudo apt-get install amarok"  type in your password and that should also do the trick.

to install a package from a deb try (from the terminal again

"sudo dpkg -i nameofpackage.deb"

This needs to be done from the folder you downloaded the deb to. If you're using firefox default this will be your desktop. From the terminal. 

"cd Desktop" 

then the instruction as before.

As for getting your mp3s playing have you read the starter guide? It can be found under help. Or search the forums for automatix, which should get you up and running a bit more quickly.

For help with your networking troubles you might try the networking forum.

Let me know how you get on.

---

### Post by jamesr on 2006-03-01
With respect to question 1
I am assuming Wireless
Is it connected to router or DSL modem?

POst the output of 
sudo ifconfig -a

---

### Post by sony102600 on 2006-03-01
Thanks for the help Beej, I will give that a shot.

And no, it is not wireless, it is hooked up directly to the campus network at  through an ethernet cord, I have been reading and it seems the problem is probably due to support for the AsRock Dual 939 on board network card....

---

### Post by sony102600 on 2006-03-01
Alright, I downloaded amarok in windows, put in on an external hard drive, and placed it on my desktop in ubuntu.  I typed in sudo dpkg -i ect ect as stated before....

it asked me for my password, typed it in, and I assumed it tried to intall, however , I got numorous messages like... amarok depends on amarok-gsteamer, kde1.bs4c2, libat3, libtaglc2, libtunpimp2c2, amarok engines... and so.. and each time it said.. however each of these items is not installed, and therefore there were errors.

As for copy and pasting the result when typing in ifconfig -a, it posted 3 things. an eth0, l0, and one other, the eht0 provided with a MAC address among other information, with packet info with it being zero... the l) provided an ap address information along with a subnet mask, the ip being like 127.0.0.15 or something like that.. and packet information, and there was packages that had been sent supposively....

I'm sorry if I'm rambling, but I can't copy and paste my results because I have no way of getting online with ubuntu....

any ideas?

---

### Post by jamesr on 2006-03-01
try copying output to a file then to floppy then to machine that links to the internet, it is only temporary but it does work.

---

### Post by Beej on 2006-03-02
It might be easier to sort your network troubles first and then try to install amarok using synaptic. If not you will need to download all the dependancies that are listed as not being resolved and install those first. Synaptic would do this for you.

I was a newbie less than a year ago, i had tried linux in the past but never a debian based distribution like ubuntu. With an internet connection and using apt-get or synaptic, ubuntu is a joy to use. Stick with it get the network problem fixed, (you will find people here very happy to help) and I don't reckon you'll look back. Amarok alone is worh the effort.

---

