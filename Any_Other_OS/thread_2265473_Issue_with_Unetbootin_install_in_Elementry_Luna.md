---
title: "Issue with Unetbootin install in Elementry Luna"
date: 2015-02-15
forum: Any Other OS
---

### Post by j-desanto0 on 2015-02-15
First off let me say that I am a complete newbie when it comes to anything Linux. Elementry was recommended to me by a buddy of mine in the google+ OSR community and have so far enjoyed it. 

I want to create a usb installer of another version of Linux (deepin) for an old laptop just to see the difference. The only issue I'm having is that Unetbootin has been stuck on "applying changes" in the software center for around 24 hours now. I can't seem to figure out a way to either force the install or to cancel it and really need some help.

I attached a screen shoot in case it helps anyone out. 

[IMG]http://i229.photobucket.com/albums/ee254/wtrjosh/6176849e-df4a-4706-a9d0-c9c0bcc23af3_zps9mrpguiy.png[/IMG]

---

### Post by kerry_s on 2015-02-15
why did you install from deb instead from software center or apt-get ?
it's probably missing dependences so it's stuck in a loop.
you need to close that, open a terminal & run:
sudo apt-get update

if there's broken stuff:
sudo apt-get -f install

install unetbootin the proper way:
sudo apt-get install unetbootin

ps:
synaptic is a better gui package manager:
sudo apt-get install synaptic

for installing *.debs gdebi is better:
sudo apt-get install gdebi

---

### Post by j-desanto0 on 2015-02-15
Thanks. I I closed out and restarted. In normal boot I got nothing but the Elementry "e" symbol. When I attempted to go in through recovery it kept cycling through a "kill" line but kept flashing the recovery menu and was able to get in. Once in, I had no sound support, my background (stock Elementry) was missing and any attempt to load graphics froze the program. Couldn't access the terminal with the ctrl-alt-t so had to go through file manager to get in. Once in terminal I used the "sudo apt-get -f install" line you gave and received the message 

e: dpkg was interrrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Ran the terminal has statred "Setting up memtest86+ (4.20-1.1ubuntu1) for about 2 hours.

Sorry for all the issues. 

> **kerry_s said:**
> why did you install from deb instead from software center or apt-get ?
it's probably missing dependences so it's stuck in a loop.
you need to close that, open a terminal & run:
sudo apt-get update

if there's broken stuff:
sudo apt-get -f install

install unetbootin the proper way:
sudo apt-get install unetbootin

ps:
synaptic is a better gui package manager:
sudo apt-get install synaptic

for installing *.debs gdebi is better:
sudo apt-get install gdebi

---

### Post by kerry_s on 2015-02-15
ya got to be careful of debs out side the system, you need to be sure there made for your version, luna is based on ubuntu 12.04lts. better to get from the built in repos or via ppa for third party stuff.

i hope you get it back up & running.

---

### Post by j-desanto0 on 2015-02-16
Thanks! Everything seems better now with Elementry, however, getting the deepin iso to actually load correctly is another issue entirely. From "no boot" to "bad karnel" this has been nothing but an issue. Kind of turned me off to it. Running Elementry is good enough for me for now.

> **kerry_s said:**
> ya got to be careful of debs out side the system, you need to be sure there made for your version, luna is based on ubuntu 12.04lts. better to get from the built in repos or via ppa for third party stuff.

i hope you get it back up & running.

---

