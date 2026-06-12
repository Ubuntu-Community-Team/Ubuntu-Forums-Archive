---
title: "HELP! Wireless + WPA"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by alhson on 2007-10-04
Hi!
First of all: I'm completely new to Ubuntu and Linux and this whole world. I am not used to doing any programming or changing any codes...

Now, I have just (successfully, I believe) installed Ubuntu on a laptop computer. But I have problems with the network. I have a wireless network card called D-Link AirPlusG DWL-G630 and the password to our network is WPA (whatever that means - don't know, don't want to know, just want it to work...).

I have done searches and tried to use what I've found (figured, if everything goes wrong I can always just reinstall the whole thing and start from scratch again). 

Somehow the computer now sees our network, but I cannot connect to it, because there is no WPA alternative in the drop down list. Also, I am not entirely sure that the computer and network card really communicate well with each other - I did some kind of test in the Terminal (just copied what I found on the net) and it said it didn't recognise the network card.

Sorry for this long question. Hope someone makes sense of it and can help me!

Thanks!

Alhson

PS: Also, the computer keeps crashing all the time - should I just go ahead and reinstall the whole thing???

---

### Post by kevdog on 2007-10-04
Couple things

1. I dont know whats causing all the system crashes.  dmesg might tell you, however a reinstall might be helpful particularly if you just installed everything.  Install 7.04 for now since its the most stable version

2. Wireless -- this is going to be your first deluge into linux, probably something you've never done before.  Getting wireless working involves
a. Installing the driver for your card
b. Configuring WPA supplicant

Our first step is to figure out what kind or wireless card or hardware you have, and then we can pick an appropriate driver.

Open up a command terminal, and type

lspci -nn
lshw -C network

Post the output and we can get started.

---

### Post by alhson on 2007-10-05
Well... I did what you told me (see attachment). The computer still keeps crashing. Could it be related to the network card?

I think I will try to reinstall - should I have the network card in there during the installation (I didn't yesterday)?

Anything in particular I should think of when reinstalling (I have a CD that my brother made for me, it's 7.04).

Thanks!

Alhson

---

### Post by Surkow on 2007-10-05
The 18th of this month a new version of Ubuntu will be released with a new network stack and new supported wireless devices. The native driver you will need can be downloaded [here]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page") but will be included in the next version of Ubuntu. In other words...you can also wait for that release if you are new to Ubuntu.

---

### Post by alhson on 2007-10-05
I guess I'll wait until the 18th then. For now, I'll try to play around with the program (without the network) and see how it works. I actually think it's the network card that is causing the crashes - but I may be wrong.

Thanks for your help! (and for the good advice at the bottom of your post too!)

---

### Post by bigken on 2007-10-05
when you say crash what happens does the pc freeze shut down tell us more of what happens I very much doubt its the network card causing this problem

---

### Post by kevdog on 2007-10-05
That network card shouldnt cause crashing and as far as Gutsy, it just contains a newer version of the driver.  In Feisty, its a couple more steps but you can easily download, compile, and install the same driver and have the same results.

 More details on the crash would be helpful

---

### Post by deep.tinker77 on 2007-10-05
Hey, I had the same problem untill about a week ago. Give wicd a try, works wonders with wireless cards that don't behave :) Good luck.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

