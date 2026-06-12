---
title: "Ubuntu install --&gt;no wireless, USB ports go dead at dual boot select screen"
date: 2008-09-21
forum: Apple Hardware Users
---

### Post by renichms on 2008-09-21
I installed Ubuntu 8.04.1 on my G4 iMac.  Then I found out Ubuntu doesn't do wireless networking (or so the enthusiastic response in the networking section would lead one to believe).  And now I'm finding out that when I want to start back up with Mac OS, the dual boot select screen kills all USB ports right before I can get the mouse over to select Mac OS.

One time, no USB ports worked.  Another, it killed everything but the keyboard and I found out the hard way that you can't select anything without a mouse (tried every key on the keyboard).  That same time, plugging mice into the USB ports in the computer itself did absolutely nothing.

I have finally gotten it to start into Ubuntu (since it won't let me choose Mac) and it all works fine now.  So basically, what the hell is going on?  Even while typing this up, I restarted again and got the mouse over the icon for Mac and it went dead before I could click.  I feel a little silly since I forgot I could just type "x" to go into Mac even when Linux is selected but...the keyboard goes out half the time too, so it'd be nice to know why this is happening.

As for the connection, since wireless is out of the question, I had to run a really long cable from one end of the house to the other to update (118 updates), thinking the update would fix it but the update didn't help the wireless any and the USB killing started only after the updates.

I apologize for ranting and probably sounding angry but this was supposed to be one of the easier to use Linux systems.  Since YDL got running smoothly on the PS3 and its only issue is no support for WPA/WPA2, I thought Ubuntu would surely be better than that, so I need some help now.  Last time I asked for suggestions in the Apple forum, I got help (nothing from the networking section), so I'm hoping someone has encountered this before and knows a way to use an Airport (not Extreme) card and USB ports.

I can provide any other details needed.  I've been networking computers for well over a decade and really haven't had problems that I couldn't figure out on my own before but Linux seems to severely limit what settings I can play with.

Thanks ahead of time for any tips.

RN

---

### Post by renichms on 2008-09-21
I also get this error every time I start up Ubuntu:
Error activating XKB configuration. 
It can happen under various circumstances: 
- a bug in libxklavier library 
- a bug in X server (xkbcomp, xmodmap utilities) 
- X server with incompatible libxkbfile implementation 

X server version data: 
The X.Org Foundation 
10400090 

If you report this situation as a bug, please include: 
- The result of xprop -root | grep XKB 
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

