---
title: "Hold my hand connecting to the internet wireless with broadband 802.11g"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by josephdeka on 2007-02-28
I installed the new ubuntu, and I cannot connect to the internet.  I can through windows of course, it searches and finds all available wireless networks in the area, but I cannot seem to accomplish this through Linux yet.

I've read a lot of the posts, and quite frankly, they are above my head at this point, I'm not sure where I am supposed to enter these texts, and many other things.  Is anyone willing to take me through in baby steps, with this?

I'd also like to know where/how best to learn about Linux inside and out.  I'm a smart guy, really I am, but Windows has dumbed things down for me so much over the last 15 years, that I don't know anything about computers other than "hit next"

If there are any posts that explain this problem in very simple terms, let me know...Everything I have read so far has required some basic knowledge of Linux, which I do not have yet.  I have enabled auto email on this, so if you need more info, ask it here, and I'll respond pretty quick!

---

### Post by Bachstelze on 2007-02-28
The first thing we need to know is the model of your wireless adapter. If you don't know it, the command *lspci* will tell you. Also, if you're lucky, your wireless adapter has native linux drivers and is readty to go, if that's the case, when you type *sudo iwconfig* in a terminal you'll see an entry that doesn't say "no wireless extensions".

By the way, [where's the terminal ?](http://psychocats.net/ubuntu/terminal)

---

### Post by josephdeka on 2007-02-28
Thanks, I'll give this a shot....I can't wait to have the wireless connection working, then troubleshooting will be so much easier, without logging off and on between windows and linux.

---

### Post by andrewlinn957 on 2007-02-28
I'm new to Ubuntu myself, and i know exactly how you feel. I think the best thing you can do is to look around on the internet for as many tutorials as possible. So far i've managed to obtain a rudimentry knowledge of how to do simple tasks just by reading posts, searching google, reading related stories posted to digg.com etc. 
As far as i know to get to the terminal (kinda like the command prompt in windows) you click applications and then go to terminal. Its called the terminal in Ubuntu. Also, 'sudo' stands for 'super user do' and requires you to enter your password so that you can perform certain tasks. Software is obtained from repositries located on the internet, and in order to download a piece of software you first have to enable a repositriry. Of course, if you're trying to get broadband working im assuming you don't have the internet with your setup yet, so i guess that isn't much help. 
anyways, thats all i know. good luck

---

### Post by josephdeka on 2007-02-28
ok, I think I've figured out the wireless adapter I have, when I typed in lspci in the terminal, I found 
Airforce one 54g
Eth 1    IEEEE 802.11b/g    essid:  off/any    nickname: "broadcom 4318
sit 0   no wireless connections

---

### Post by Bachstelze on 2007-02-28
All right, it's a Broadcom car, they're a bit more troublesome to get working... You'll have to reboot in Ubuntu to do a few things :

-> Run the commands *lspci* and *lspci -n* and copy the *exact* ouptut you get, you can copy/paste it to a text file.

-> Blacklist the bcm43xx driver. Here's how to do it :

First, open the needed file in a text editor :

```
sudo nano /etc/modprobe.d/blacklist
```

Go to the bottom of the file and add a line like this :

```
blacklist bcm43xx
```

Then save the file (Ctrl+O, Enter to confirm) and exit nano (Ctrl+X).

-> Download [this](http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb) and [this](http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb), copy them to a dir somewhere you can access from Ubuntu and install them with *sudo dpkg -i*.

When you say "the new ubuntu", I assume you use Ubuntu 6.10 (aka Edgy Eft), if you're running Ubuntu 6.06 (aka Dapper Drake), download [this](http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb) instead.

---

