---
title: "No internet on MacBook. Is Airport the problem?"
date: 2010-07-22
forum: Apple Hardware Users
---

### Post by wozij on 2010-07-22
Hey people,

I'm new here but I'll try my best to be as specific as I can.
I installed Ubuntu 10.04 on my MacBook6,1, next to the Mac OS X. So i have two OS. The way I connect to internet on Mac OS X is via Airport. If I'm correct I have an Airport Extreme. Next to that the number 802.11n seems to be important when I read other threads.

The thing is: I can't connect to internet using Ubuntu Linux. It can't seem to see any networks and I think Airport isn't detected at all.

After reading a few other threads from people on a Mac using Airport with problems I tried a few things:

1. I read somewhere that I should install the package b43-fwcutter, which is on the Ubuntu CD. I tried but it failed. It gave me the message:
*Failed: name or service not known.*

2. Using the terminal I should enter the line:
*sudo apt-get install bcmwl-kernel-source*
This package was not known.

3. I tried to install kernel which was in in the folder restricted/b/bcmwl. It said that this wasn't possible.


Is there anyone with an idea on how I can get my internet to work?

Thanks in advance people,
Wozij

P.S. or should this thread be in the internet and wireless department?

---

### Post by cdnaerogeek on 2010-07-22
See this page for more info:

[https://help.ubuntu.com/community/MacBook6-1/Lucid]("https://help.ubuntu.com/community/MacBook6-1/Lucid")

The way I got wireless working on my MacBook Pro was to hook up to the internet via ethernet cable and download the necessary drivers. It's generally good practice when installing or upgrading Ubuntu to have that wired connection available since wireless support tends to be tricky on some machines.

---

### Post by zeroti on 2010-07-23
you might also want to right-click the wireless icon in the menu and make-sure that the "Enable Networking" and "Enable Wireless" are selected.

---

### Post by wozij on 2010-07-26
> The way I got wireless working on my MacBook Pro was to hook up to the internet via ethernet cable and download the necessary drivers. It's generally good practice when installing or upgrading Ubuntu to have that wired connection available since wireless support tends to be tricky on some machines.

Thanks! That worked. So simple.

---

