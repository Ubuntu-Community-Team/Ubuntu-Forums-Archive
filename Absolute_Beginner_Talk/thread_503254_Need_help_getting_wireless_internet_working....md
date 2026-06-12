---
title: "Need help getting wireless internet working..."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by valkz0r on 2007-07-17
So basically what I have is a full install of Ubuntu sitting on my computer and I can't use it because I can't get internet on it :(.  I have the Netgear WG111v2 Wireless USB Adapter and the drivers don't work with Linux so no go...I've researched around and found that I need to use a program called Ndiswrapper (I think) but the problem is that I don't know how to install it so I'm pretty SOL.  Any help would be appreciated.

thanks,
valk

---

### Post by valkz0r on 2007-07-17
*bump*  I need serious help with this...

---

### Post by anewguy on 2007-07-17
Hi, I'm relatively new here myself, and I had to use ndiswrapper to get my wireless working as well.  I did a yahoo search on "ubuntu ndiswrapper Netgear WG111v2" and it came up with various hits.  Perhaps the following, while not for the latest release of Ubuntu, will help you:

[http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html](http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html)

Hope it helps!:)

Edit:  forgot to mention, the commands that show on that page you will need to run in a terminal.  To get to a terminal window, click on "Applications", then just move over and click "terminal".

---

### Post by ugm6hr on 2007-07-17
That link from anewguy looks promising.  As mentioned - all lines that start with *sudo ....* need to be entered in Terminal.  Couple of edits though - if you don't already have internet on the computer.

To achieve this step:
> Install ndiswrapper, specifically ndiswrapper-utils-1.8
sudo apt-get install ndiswrapper-utils-1.8

Go to the following sites and click on the appropriate Architecture (presumably i386 for most people) in the download table, and then on a download mirror to get these packages.

[B][http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)[/B]

Download to wherever, and then just double click on them in order.

The rest should work as is.  I think further detail is provided in the link back to the forum.

---

### Post by Jose Catre-Vandis on 2007-07-17
This thread will cover everything you need to know about getting going with a WG111v2 (if that is what it is! - you'll need to read the thread to see what I mean)

[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

---

### Post by valkz0r on 2007-07-17
Ok, thanks guys...but I still need to figure out how to install Ndiswrapper...do I just put "ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb" on my desktop then run *sudo apt-get install ndiswrapper-utils-1.8* or what?  Sorry but I'm **really** new to this...

---

### Post by BlueNoteExpress on 2007-07-17
You should be able to install from .deb file by just double-clicking on the .deb file.

---

### Post by ugm6hr on 2007-07-18
> Ok, thanks guys...but I still need to figure out how to install Ndiswrapper...do I just put "ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb" on my desktop then run sudo apt-get install ndiswrapper-utils-1.8 or what? Sorry but I'm really new to this...

> **ugm6hr said:**
> Download to wherever, and then just double click on them in order.


As above.

---

### Post by valkz0r on 2007-07-25
Ok, so here's where the problem stands: when I click the ndiswrapper .deb it installs fine but when I try to run any ndiswrapper commands in the terminal I get this-
"Error: no versions of ndiswrapper found!"
Anyone know what I'm doing wrong here? :(

---

### Post by ugm6hr on 2007-07-26
> **valkz0r said:**
> Ok, so here's where the problem stands: when I click the ndiswrapper .deb it installs fine but when I try to run any ndiswrapper commands in the terminal I get this-
"Error: no versions of ndiswrapper found!"
Anyone know what I'm doing wrong here? :(

Have you installed both .debs linked above (-common and -utils)?

---

### Post by valkz0r on 2007-07-26
...both...I forgetted...yea I'm gonna do that now.

---

### Post by Staff on 2007-08-29
to install ndiswrapper easily, insert your ubuntu install disc into the cd drive ( after boot up ) and run synaptic ( found in system - administration - synaptic package manager ) and scroll down until you find Ndiswrapper. check the box for install and click the 'apply' button at the top.

---

