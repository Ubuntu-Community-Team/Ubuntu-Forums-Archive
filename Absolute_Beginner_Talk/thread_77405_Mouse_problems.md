---
title: "Mouse problems"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by natman on 2005-10-16
Hi i have brezzy installed on my compaq (amd 64 ) laptop with a usb mouse,and when i start up the mouse does not light up or anything is dead.
Is there anyway to get the usb mouse working in brezzy.?

Also i get the following message at start up
" USB HC takeover failed ! "

---

### Post by ecobuntu on 2005-10-16
how about:

sudo dpkg-reconfigure xserver-xorg

see if that does anything

---

### Post by natman on 2005-10-17
Nope it did nothing,

But i started up ubuntu this morning, and i got a nice yellow looking ubuntu and a yellow loading word, any all the stuff loaded fine and my mouse worked.
So i rebooted and got the yellow ubuntu word, the it paused went back to a back screen with white print and one of the frist lines says
"
USB HC takeover failed ! (BIOS / SMM bug)
cant reset
........ fail, -16 
"
So can anyone tell me what to do get my mouse working
( i am just after reinstalling the badger that did nothing )

thanks:

---

### Post by SilentCacophony on 2005-10-17
> and when i start up the mouse does not light up or anything is dead.

That would lead me to believe that there's a problem with the mouse itself, or the hardware USB controller. I don't see how the software level would affect whether the lights on the mouse operate or not.

> USB HC takeover failed ! (BIOS / SMM bug)

This leads me to believe that the firmware level (BIOS) may also be a possible culprit. Have you looked through your BIOS settings to see what, if any, settings there are regarding USB and mice?

In any case, I've seen that you have posted this issue several times, but I've not seen anyone else with this issue, so it looks as if it's a problem fairly unique to your setup. In such cases, careful 'googling' may be helpfull.

Personally, I have an early Logitech USB optical mouse, it it was autoconfigured without a problem, and I supect that's the usual scenario.

EDIT - One thread I found that may be related to your problem:

[http://ubuntuforums.org/showthread.php?t=26374](http://ubuntuforums.org/showthread.php?t=26374)

Seems some people need to upgrade thier BIOS.

---

### Post by natman on 2005-10-17
As for the mouse and or usb hardware, i dont think there is any problem there, as i have a dual boot in XP also and the logitech mouse is always dectected fine there and i never had a prob with any usb device in windows before.

Yes i googled for a while last night, i saw a lot of people talking about the BIOS , the i read ur link thread, saw some one with a compaq presario (same as me ) and they got the problem solved via BIOS update F34. 
The thing is i am very new to computers ( only windows experience before, linux for one week ) and am very scared of messing around with set up stuff, but l have some well informed friends, i will ask their advice.
Plus most of the stuff on the google matches made no sense to me whatsoever.


Thank you for all you help

---

