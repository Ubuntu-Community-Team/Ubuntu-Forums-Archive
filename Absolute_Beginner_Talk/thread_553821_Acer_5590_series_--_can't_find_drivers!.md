---
title: "Acer 5590 series -- can't find drivers!"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by MechChap on 2007-09-18
Hello to gurus and newbies out there. This is my official 1st post :KS

I've installed ubuntu on my Machine - Acer 5594WXMi. 

To help you guys help me with my troubles, I'll detail a simple background knowledge of my previous experience with computers. 

1) I migrated from XP - which also means, I am not used to command lines and hence I have the "microsoft does it for you" mindset.

2) Ubuntu is a totally new environment to me. I have no idea whatsoever so please give me a more detailed explaination when helping me lol.

3) I'll list my hardware specs if they may help:

Model: Acer 5594 WXMi taken from the 5590 series
-Core 2 duo 1.83GHz 
-ATI X1600 graphics card (Was a pain to set up!)
-1 GB DDR2 ram
-120 GB HDD
-Orbicam 
-Bluetooth

Now to the main dish a.k.a problem:

I've been searching drivers for my laptop for the past few days now and I can't find any. Seems like no one uses this model on linux or something...

To shorten things down:

1) Fn key not working. Only the brightness control works. 
2) Bluetooth and Wireless switches not responding. (I could get the wireless to work but not the bluetooth.)
3) NumLock seems to work but instead of printing out numbers, it moved the mouse... "4" moved the mouse left, "8" moved up, "3" moved right and so on...

now... can anyone tell me where to start or help me find the drivers or most importantly, tell me what's wrong so i can learn.

---

### Post by overdrank on 2007-09-18
> **MechChap said:**
> Hello to gurus and newbies out there. This is my official 1st post :KS

I've installed ubuntu on my Machine - Acer 5594WXMi. 

To help you guys help me with my troubles, I'll detail a simple background knowledge of my previous experience with computers. 

1) I migrated from XP - which also means, I am not used to command lines and hence I have the "microsoft does it for you" mindset.

2) Ubuntu is a totally new environment to me. I have no idea whatsoever so please give me a more detailed explaination when helping me lol.

3) I'll list my hardware specs if they may help:

Model: Acer 5594 WXMi taken from the 5590 series
-Core 2 duo 1.83GHz 
-ATI X1600 graphics card (Was a pain to set up!)
-1 GB DDR2 ram
-120 GB HDD
-Orbicam 
-Bluetooth

Now to the main dish a.k.a problem:

I've been searching drivers for my laptop for the past few days now and I can't find any. Seems like no one uses this model on linux or something...

To shorten things down:

1) Fn key not working. Only the brightness control works. 
2) Bluetooth and Wireless switches not responding. (I could get the wireless to work but not the bluetooth.)
3) NumLock seems to work but instead of printing out numbers, it moved the mouse... "4" moved the mouse left, "8" moved up, "3" moved right and so on...

now... can anyone tell me where to start or help me find the drivers or most importantly, tell me what's wrong so i can learn.

Hi and welcome this link may help with the blue tooth 
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
Good luck! :)

---

### Post by MechChap on 2007-09-19
I tried that bluetooth setup tutorial but didn't seem to work. I'll have another go at it and report back.

Meanwhile, I've tried setting up the Fn Keys by going through this site: [https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch)
None of the methods in there worked for me. Through the second method, it printed out 0x9c which was my Fn Key. But When I tried combinations like Fn - Volume/mute button, it doesn't seem to work. I tried typing Fn Key into the Keyboard short cut, doesn't work either. 

When i moved on to the "identifying your laptop" section, here's what I've got:
$ sudo dmidecode -s system-manufacturer - Acer 
$ sudo dmidecode -s system-product-name - TravelMate 3290
$ sudo dmidecode -s system-version - 0100

---

