---
title: "mp3 player doesn't charge via usb after upgrade"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by toscy on 2007-04-21
I have a Microsoft Zune which charges via a usb port. I've tried it on several ports but it just doesn't charge anymore after upgrading to Feisty Fawn. It DOES know it's plugged in and charges one bar but it stops then.

A zune will basically charge with anything with a USB port and powersuch as  a 360 so the fact that I have ubuntu doesn't matter, it worked on edgy. But something from upgrading has made it stop charging.

ACTUALLY I've noticed that the Zune keeps randomly lighting up whilst plugging in (like when you first plug it in and it starts charging) and it will sometimes do one bar before just stopping. I've tried fiddling with the cable but it's not that. Nothing is wrong with the Zune either, it's been tested.

Thanks for any help!

---

### Post by Pobega on 2007-04-21
Have you tried it with the 360 lately? See if the same problems occurs with the XBox, and then report back to us what happens.

---

### Post by orb9220 on 2007-04-21
Sorry I just plugged in my sansa e250 which also charges by usb. Seems to be charging fine.
I let you know if it doesn't do a full charge.

At this point If I was you is to post a bug at launchpad since it was working and stopped in fiesty.

---

### Post by toscy on 2007-04-21
Thanks for the responses.

Pobega, I don't have a 360 (I just know you can do it like that) but I do have a Windows machine which charges it fine.

orb9220, thanks, I'll wait for any other responses first though before I do that.

---

### Post by Pobega on 2007-04-21
I really have no idea what can be going on then. Is it possible to try the LiveCD to see if it works?

---

### Post by toscy on 2007-04-22
> **Pobega said:**
> I really have no idea what can be going on then. Is it possible to try the LiveCD to see if it works?

I guess that's my best option, I'll have to get round to downloading it first and then doing it but I'll let you know how it goes. Thanks.

---

### Post by Pobega on 2007-04-22
Well, I didn't mean it like that.

I mean if it works on the LiveCD then you're most likely missing a package or something like that, although I doubt that's what it is.

This really doesn't sound right to be to be honest, since it is more of a hardware thing then a software thing; Is Ubuntu even picking up your Zune at all?

---

### Post by BeastlyKings on 2007-04-22
Hi, I am having the same problem and I DO have a 360 and it does charge on the 360.
I didn't upgrade though, I installed the latest and greatest Ubuntu 7.04 downloaded from the websites main download page.

I did a test and the Zune will charge fine when the PC is going through post and the bootloader, but the second that Ubuntu starts to load, with its little loader bar, The Zune stops charging.

I am curious to see what the prob is because it is REALLY bugging me.

EDIT:
OK, I just did a test to see if Ubuntu even sees the Zune.
I ran "lsusb" to see what it gave me.

root@tom-laptop:~# lsusb
Bus 001 Device 011: ID 045e:0710 Microsoft Corp. 
Bus 001 Device 010: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 004: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 002: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000  


And there it is, "Microsoft Corp.".
Why isn't it charging then?

---

### Post by Zune-Online.com on 2007-04-23
I use debian-amd64 with 2.6.20 kernel, but it charges without problems.

Run lsusb -v . In the Microsoft Zune section it should be a "MaxPower" field. Mine is:
    MaxPower              500mA

I suppose yours has to be 100 mA so Zune can't charge. If this is your problem I found this little prog, acharge, to help you. I haven't tested it since I don't have this problem.

[http://ubuntuforums.org/showthread.php?t=371255](http://ubuntuforums.org/showthread.php?t=371255)

---

### Post by nelio2k on 2007-04-23
I have a zune, and the same problem after updating to feisty.

I realized that whenever i run lsusb command, it'll probe the zune to charge once, and stop. So, if you keep on running the lsusb command, or just write a while loop scrip to call it, maybe output the messages to a file, then the zune will keep on charging.

As an alternative, I tried the acharge program you mentioned above. It does the same thing and only charges once and stop, since for me, the usb port is already providing max of 500mA. 

It seems to be a bug in the ubuntu distro, not with the kernel (since previously a debian guy said it works ok for him, assuming he's got the latest linux kernel as well).

So for now, I charge it under windows... :-P since Zune doesn't necessarily work under linux anyway.

---

### Post by Evil Dax on 2007-05-06
My telephone also does not charge anymore since upgrading to Feisty. Also the aCharge thingy doesn't work.
Any more ideas on this??

---

