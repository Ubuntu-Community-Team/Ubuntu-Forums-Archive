---
title: "Updating Breezy"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-05-24
Hi All,

Another newbie question.. :) 

does ubuntu update itself automatically, or do I need to do it? If so, how often, and how do i go about it? 

thanks

Patrick

---

### Post by ProjectGod on 2006-05-24
i heard automatic updates can be selected from some source or other... 

but to satisfy the "nerd" in me i use the command line :mrgreen: 

[www.ubuntuguide.org](www.ubuntuguide.org) has everything you 'll want...

but to cut it short... you'll have to add the repositories by going to the terminal and editing the /etc/apt/source.list

then you'll be able to use the following command at the terminal
[B]
sudo apt-get update

sudo apt-get upgrade[/B]

you may need to enter YOUR user password when prompted to... the upgrade option upgrades every package on your ubuntu linux... first time i did it initiated a download of 80+ megabytes...

use the 

**sudo apt-get update **regularly

---

### Post by bluenova on 2006-05-24
Unless you turned off the update manager, then ubuntu will inform you with an icon in the top right of your screen when updates have been detected in the repositories.

---

### Post by ozPATT on 2006-05-24
haha, i think deep down in me also lies a nerd... 

i have added some repositories, but not from the command line. I will have a look at the ubuntu guide for help on this, but how am i to edit the /etc/apt/source.list? I will have a look on the guide, if it says it in there, ignore this question, as I am sure I will come across it. 

if i just did sudo apt-get update now, before adding any repositories, would that update everything?

---

