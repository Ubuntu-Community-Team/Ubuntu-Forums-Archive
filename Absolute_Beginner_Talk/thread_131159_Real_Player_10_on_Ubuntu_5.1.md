---
title: "Real Player 10 on Ubuntu 5.1"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by ubuntu_newbie_2006 on 2006-02-15
Hi Everyone.
I'm using Ubuntu 5.1  and just downloaded the BIN file for RealPlayer10 for linux. ([www.real.com/linux)](www.real.com/linux)).

To install, I did the following (as instructed on Real's Website)
 - Opened a terminal and ran: "**chmod a+x RealPlayer10GOLD.bin**"
 - Then I typed "**./RealPlayer10GOLD.bin**"

I get this message error:
[FONT="Courier New"]  "error while loading  shared libraries: libstdc++.so.5:
   cannot open shared object file: No such file in  
   directory"[/FONT]

 Is RealPlayer compatible with Ubuntu?

---

### Post by Protostar on 2006-02-15
[QUOTE=ubuntu_newbie_2006]Hi Everyone.
I'm using Ubuntu 5.1  and just downloaded the BIN file for RealPlayer10 for linux. ([www.real.com/linux)](www.real.com/linux)).

To install, I did the following (as instructed on Real's Website)
 - Opened a terminal and ran: "**chmod a+x RealPlayer10GOLD.bin**"
 - Then I typed "**./RealPlayer10GOLD.bin**"

I get this message error:
[FONT="Courier New"]  "error while loading  shared libraries: libstdc++.so.5:
   cannot open shared object file: No such file in  
   directory"[/FONT]

 Is RealPlayer compatible with Ubuntu?[/QUOTE]

Sure it is.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Click the above link and scroll down until you get to the Real Player section. It will tell you how to install the player.

---

### Post by bluevoodoo1 on 2006-02-15
looks like you need libstdc++5...

sudo apt-get install libstdc++5

---

### Post by ubuntu_newbie_2006 on 2006-02-15
Worked like a charm. Thanks. :-D

---

