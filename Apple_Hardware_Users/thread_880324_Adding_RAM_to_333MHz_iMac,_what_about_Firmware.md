---
title: "Adding RAM to 333MHz iMac, what about Firmware?"
date: 2008-08-04
forum: Apple Hardware Users
---

### Post by crios on 2008-08-04
I have a 333MHz iMac with 64MB of RAM running Xubuntu. It actually runs pretty well except that it's sloooowww. I want to add more RAM and I've seen that you can add up to 512 RAM. I'm planning on buying 2 x 256 sticks of RAM from Other World Computing, the one requirement that I've seen is that you need to have Apple firmware 1.2 installed. The problem is that I already have Xubuntu installed on the iMac. How can I check what version of Firmware is installed or is the issue moot because Xubuntu already installed a different type of firmware (open firmware?)? I'm a little unclear on this prerequisite. 

Any and all help is appreciated.
Chris

---

### Post by oswaldkelso on 2008-08-05
> I have a 333MHz iMac with 64MB of RAM running Xubuntu. It actually runs pretty well except that it's sloooowww.

I have the same machine with 256.mb, and yes its dog slow with a stock Ubuntu install. You need a window manager or lighter desktop  and a base install to have an enjoyable experiance.

I have Debian Lenny and Blackbox or e17 and it runs great, You can do the similar with Ubuntu.

>  I want to add more RAM and I've seen that you can add up to 512 RAM. I'm planning on buying 2 x 256 sticks of RAM from Other World Computing, the one requirement that I've seen is that you need to have Apple firmware 1.2 installed.

You can have upto 1gb depending on the ram sticks and macine version its hit and miss. To be honest due to the processor limitations a ligher system is more important. Also  buying more ram can be more expensive than the value of the machine a single 256mb stick is what I would consider a good comprimise.

>  The problem is that I already have Xubuntu installed on the iMac. How can I check what version of Firmware is installed or is the issue moot because Xubuntu already installed a different type of firmware (open firmware?)? I'm a little unclear on this prerequisite.

As far as I know you can check your firmware in osx, somone else may be of more help on this, you can only update your firmware from osx. I would suggest you read the link in my sig as it covers many problems around the machine.

If you want a quick and slick installation e17 is the way to go faster than xubuntu but does need a little tweeking. If you want pure speed one of the "boxes" and a  file manager. Rox-filer is my favorite but does take a little learning. Some very good how-to's in the debian forum just search "rox". Many people try it for 2 mins and switch back to somthing else but give it 2 weeks and investigate its power.

---

### Post by tiresia on 2008-08-05
Here is a useful link for you iMac: [http://support.apple.com/kb/HT1395?viewlocale=en_US](http://support.apple.com/kb/HT1395?viewlocale=en_US)
Anyway you can update your firmware only with OS9. Yes the "up-to-date" Firmware for your iMac is 1.2, and I guess it's the one that it's already installed. 
BTW, the firmware has nothing to do with "Open Firmware". Open Firmware is a software that acts as BIOS in PC, that starts before the OS and informs it about the Hardware.
I can only confirm what Oswaldkelso says!

---

### Post by crios on 2008-08-05
Thanks,
I think I'm going to go with your 1 stick of 256 suggestion. I might try another stick later on but I'll see how this goes first. The reason I went with Xubuntu was because I'm not real technical and so I needed something that was relatively easy to get up and running. This machine is basically a email and internet machine for my wife who is TOTALLY non-techy. She does all right on computers but I was also looking for something that is easy for her to get and use. 
[SIZE="1"]If I change it up on her now she might kill me.[/SIZE]

So about the firmware... Could I run OS X on this machine? I don't think so... I do have an OS 9 disk. If I need to upgrade the firmware I could probably reinstall OS 9 and then do it from there. Before I do that I need to figure out how to find out what version of the firmware is installed on the machine. I'm guessing that the firmware is up to date because Xubuntu wouldn't have installed on it if it wasn't (according to some Xubuntu installation posts that I've read).

By the way, how can I check if 256 stick of RAM is being seen after I install it? I'm going to leave the 64 in so it should still work after I add the 256. Is there something like the Apple System Profiler in Xubuntu or is there a terminal command that I can type in that will tell me how much RAM is installed?

---

### Post by tiresia on 2008-08-05
> **crios said:**
>  So about the firmware... Could I run OS X on this machine? I don't think so... 
Yes, you can! But OS9 is fine if you want just to check your firmware.

> **crios said:**
> I do have an OS 9 disk. If I need to upgrade the firmware I could probably reinstall OS 9 and then do it from there. Before I do that I need to figure out how to find out what version of the firmware is installed on the machine. I'm guessing that the firmware is up to date 

I think too! Anyway if you want to reinstall OS9 and reinstall Xubuntu:popcorn:, you will find the Firmware-Version in the Apple System Profiler 

You should see something like this:

ROM revision: $77D.44F1
Boot ROM version: 3.0.f3 (or 3.0.b2 if update not installed)
Mac OS ROM file version: 1.1

Here a useful link:
[http://www.uktsupport.co.uk/apple/faq/imac.htm](http://www.uktsupport.co.uk/apple/faq/imac.htm)

> **crios said:**
> By the way, how can I check if 256 stick of RAM is being seen after I install it? I'm going to leave the 64 in so it should still work after I add the 256. Is there something like the Apple System Profiler in Xubuntu or is there a terminal command that I can type in that will tell me how much RAM is installed?

You have many ways: System Tools > System monitor, or 
for the processor
```
cat /proc/cpuinfo
```

for the RAM
```
cat /proc/meminfo
```

or even easyer
```
free
```

---

### Post by crios on 2008-08-05
Thanks Tiresia,
That's exactly what I need.

---

### Post by stream303 on 2008-08-05
That additional ram should help out greatly.

In regards to the firmware update, see this:

[http://support.apple.com/kb/HT1395](http://support.apple.com/kb/HT1395)

With it, you'll be able to run osx, (how well is another matter) but as was pointed out, you can only do the firmware upgrade from an existing mac os on the hard disk.

Heed the warning NOT to put any sort of OSX install disk, or 3rd-party utility disk in any older iMac that hasn't had this firmware upgrade first.

---

### Post by crios on 2008-08-06
I got my RAM and decided for the heck of it I'd go ahead and get 2 sticks of 256. I installed them and powered up the machine and it sees the BOTH!
I'm feeling quite proud of myself right now and my little old iMac has gotten quite peppy.



:guitar:

---

