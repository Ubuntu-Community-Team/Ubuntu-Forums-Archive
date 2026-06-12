---
title: "Usb"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Howard Edwards on 2007-10-01
I've just installed ubuntu 7.04 in a spare PC that is only USB 1 at the moment. I can easily upgrade it to  USB 2 with a pci card. I am quite keen to get more skillful with Ubuntu  - I think Linux is going to be more important in the future particularly if all the stories I hear about the V - word are true !
I have one question:  Should Ubuntu automatically be able to work with the USB sockets on my machine ? I tried to connect the machine to my broadband wireless router by plugging a wireless USB stick into one of the uSB sockets and the machine does not recognise the fact the I have plugged it in.  
Warning - you are now reading the posting of a complete newbie when it comes to  Linux, and in a sense,  I feel as if I am starting computers from scratch after having been joined at the hip with MS Windows since version 3.1 !!

Thanks 
Howard

---

### Post by Het Irv on 2007-10-01
Try plugging into a wired port and downloading updates.  Also check to see if your wireless can send and recive information before moving.

---

### Post by Damanther on 2007-10-01
Just want to get a little more info from you. Then maybe we can help a bit more.

You mentioned your router as well as a usb stick. Do you mean to say that you are plugging the usb connector from the router to the usb port on your Ubuntu machine?? Or are you plugging a some other usb device like a wireless adapter into that port?

Welcome to Ubuntu by the way. Hope we can help.

---

### Post by kebes on 2007-10-01
> I tried to connect the machine to my broadband wireless router by plugging a wireless USB stick into one of the uSB sockets and the machine does not recognise the fact the I have plugged it in.
Ubuntu should automatically detect and configure your USB controller and ports. However, when it comes to wireless USB devices, Linux compatibility is not 100%.

You can check the Ubuntu hardware compatibility list here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

See if you can find your wireless adapter on the list. There may be information on how to get it working.

> I can easily upgrade it to  USB 2 with a pci card.
I don't think that will help. As I said when it comes to wireless the issue is having a driver for the device in question. If you are willing to buy a PCI card, then you could get a new wireless card for the computer. Just check the compatibility list and pick something that has "out of the box" Ubuntu support. That way you can be confident that Ubuntu will properly detect and configure it.

> I am quite keen to get more skillful with Ubuntu  - I think Linux is going to be more important in the future 
I'm glad you're keen and interested! Welcome to Ubuntu! It takes time to learn a new OS, but it's very rewarding, too. If you have any more questions, feel free to ask.

---

### Post by Howard Edwards on 2007-10-01
Thanks for the quick responses.  I'm trying to get a wireless usb stick to talk wirelessly to my broadband router which is working fine at the moment  with a wired ethernet connection to my wife's machine (the 'main' machine) and also a wireless connection to my laptop which has built-in wireless.  The little led on the wireless usb stick plugged into my linux machine has not come on at all.  I'm not sure as to whether this is a hardware problem or whether Linux is not talking to the usb system in the machine. When I right click on the network icon at the bottom of theubuntu screen, the menu does not offer an 'enable wireless' option - only 'enable network'. 
Hope this helps.
Got to go to work this evening - so have to power down, now. Will get back on tomorrow !

---

### Post by Howard Edwards on 2007-10-02
Thanks for all your help - much appreciate it - I've now got a lot of food for thought.  
I didn't realise how quickly this board fills up - had to search quite a few pages back !!

---

### Post by darren1270 on 2007-10-02
> **Howard Edwards said:**
> The little led on the wireless usb stick plugged into my linux machine has not come on at all.


If your usb stick is 2.0 then it will not work ...... hence the led not lighting up for you.  It is the same for windows.... had a customer call and say their brand new usb wireless stick is not working... find out it is 2.0 and their usb ports are 1.1.  changed to a usb 1.1 stick and worked great.

Good Luck
Darren

---

