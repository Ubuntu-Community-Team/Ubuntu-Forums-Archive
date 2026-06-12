---
title: "Few questions - system seems slow"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by bellalamb on 2007-06-14
Just started to use Ubuntu  v7.04

Installed on Compaq nx9010, Celeron 2.8G, 768Mb Ram, 40G hard disk, built in 100Mhz Lan, Netgear WPN511 wireless adapter

Everything appears to work, but seems to be much slower than the WinXP system the was previously on this computer.
for example 
adding a printer - takes almost 3 minutes to read the printer database
firefox takes seconds to first respond to keys after page loaded

also have a question re jetdirect 3 port printer server
how do you get to print on port other than port 1

overall very impressed with Ubuntu - just would like to get it running faster

---

### Post by hyper_ch on 2007-06-15
Hmmm, open a terminal, enter this command:

```

sudo apt-get install htop

```
It prompts you for a password (sudo is the way of running something as administrator) and it will be your user password that you have to enter

Once htop is downloaded and installed type in the terminal:

```

htop

```

It will then nicely show you what process uses how much cpu and stuff... you have then also directly the option of "nice".

Just click on a process and hit the nice+ or nice- button... the higher nice is, the less priority does that process have... however first see what is actually using all your cpu :)

---

