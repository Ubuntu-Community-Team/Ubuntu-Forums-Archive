---
title: "Windows 7 takes 5 minutes to load!"
date: 2011-09-04
forum: Any Other OS
---

### Post by Ieroglif on 2011-09-04
Hi there,
  Sony VAIO VPCS11C5E
  Intel(R) Core™ i7 CPU         M 620 @ 2.67 GHz
  6 GB of RAM, 64-bit Operating system
  My computer is about 1,5 years old and suddenly won't start Windows 7 Professional or only starts it after about 5 minutes of loading.  I've run through several attempts to solve this problem and here are some of the results I get:
  -         The system restore cannot solve this problem
  -         It can’t sort it by returning to the earlier date (the date when it worked fine)
  -         The tests say that there are errors in Windows Device Manager
  -         USB and Surface Scan Tests failed (E-USB-001 & E-HDD-004)
  I wonder if it could happen while I was going through security X-Ray at the airport with my laptop in sleep mode?
  Also the computer now is operating slower than usual.
  Is this Windows 7 problem or is it my laptop? What can be done?
  Thanks,
  Irina

---

### Post by jefelex on 2011-09-04
Why are you asking that here?  The whole point of Ubuntu is to completely replace Windows.  You say your computer is 1½ years old, it should run 11.04 with no problems at all - and boot in less than 30 seconds. 

Windows has seen it's day - it is old and bloated software, and not worth the kind of money they are asking for it.

Try the Ubuntu live image - burn it to a USB stick (preferably a USB2) and even from the usb, it will blow the doors off W7

I purchased 2 brand new laptops at Christmas last year, and before I even turned them on, deleted the W7 install and put Ubu 10.04 on them.  They both have worked perfectly since and have never crashed. That said, I can't say I have experienced the W7 problems!

Hope you get it sorted out!

John :-)

---

### Post by jefelex on 2011-09-04
> **Ieroglif said:**
> Hi there,
  Sony VAIO VPCS11C5E
  Intel(R) Core™ i7 CPU         M 620 @ 2.67 GHz
  6 GB of RAM, 64-bit Operating system
  My computer is about 1,5 years old and suddenly won't start Windows 7 Professional or only starts it after about 5 minutes of loading.  I've run through several attempts to solve this problem and here are some of the results I get:
  -         The system restore cannot solve this problem
  -         It can’t sort it by returning to the earlier date (the date when it worked fine)
  -         The tests say that there are errors in Windows Device Manager
  -         USB and Surface Scan Tests failed (E-USB-001 & E-HDD-004)
  I wonder if it could happen while I was going through security X-Ray at the airport with my laptop in sleep mode?
  Also the computer now is operating slower than usual.
  Is this Windows 7 problem or is it my laptop? What can be done?
  Thanks,
  Irina

In response to your questions, I seriously doubt that there is anything physically wrong with your computer. The security scanners will not affect a computer in that way, I do not agree with the idea of being microed going into an airplane, but since the scanners use Xrays, they will not affect the data on your HD or your USB drives. 

I personally think it's a Micro$oft ploy to self destruct after a certain random amount of time, to keep computer technicians employed! :confused:

---

### Post by 2F4U on 2011-09-04
When you say a surface test failed, do you mean that a health check on your hard disk failed? If that is true, it could explain the long startup times. If an OS encounters a bad sector, it marks the sector and tries to find another one. This takes time and the more bad sectors the more time it takes.
However, this has nothing to do with X-Rays. My guess would be that the laptop was moved while it was running and a head crash occurred.

---

### Post by texaswriter on 2011-09-04
Slow laggy Windows boots are nothing new. 

Although, I haven't had much problems with Windows 7 computers at work, but corporations usually have a "freeze" windows or equivalent.. And they also manually push their own Windows updates (which one should always do, manually pushing updates for operating system or programs in order to best evaluate the effect). 
 
Windows 7 is also usually better than Vista. 

On the other hand, Windows 7 installs usually blow up in my face within months, refusing to boot or something silly. 

But seriously, the only time I ever have slow boots with Linux is when I install them to a USB disc. It's never taken anywhere near 5 minutes though...

---

### Post by NightwishFan on 2011-09-04
I doubt it is something the airport did. This sounds to me like perhaps you have a failing hard disk? If you have errors in device manager perhaps you are lacking required drivers? Have you tried identifying the devices in question and reinstall them from your vendors web page?

---

### Post by shobon on 2011-09-04
Go to My Computer, right click on your C: drive and do a disk cleanup. Then go to the Tools tab and run the Error-check (by clicking check now). From there click all the boxes and press start. It'll tell you you need to reboot, so do that. This can/will take a long time.

Then install CCleaner and Defraggler, and run them both in that order.

I do this a few times a month, and Windows 7 is always running like new.

---

### Post by Allavona on 2011-09-04
The best advice to Windows users. "Just simply shutdown and reboot. Do not suspend, hibernate, or sleep, just shutdown."

CCleaner and defraggler were mentioned. These help to keep the system free of useless junk and to reorganized the file system so its faster and more efficient. (One of the pains of an NTFS setup)

Also a quick perusal of you startup programs just may amaze you. I had a buddy that had just about every program you can imagine start with the computer! You only need a couple with windows (at the very least.)
1. Your OS (obviously)
2. Security program(s).
3. All needed drivers. (another obvious one)

Everything else can be started when needed and shut down when done. Windows itself uses a truckload of resources itself, there is no need to tie up more than need be.

Or it could be something bad like a head crash/failing disc as mentioned earlier.

---

### Post by oldfred on 2011-09-04
I rarely use my XP anymore but Ubuntu boots 10 to 20sec faster after running chkdsk as shobon suggests. The mount is now quicker.

Also Windows NTFS partitions slow down a lot if they do not have lots of room. At least 30% is suggested, it starts to slow down at 20% and  at less than 10% everything is slow & chkdsk may take forever (some have reported days on large drives).

---

### Post by drawkcab on 2011-09-04
I'm about a year and a half into win7 on one of my partitions and I've had none of these problems.

What I would suggest is backing up all of your data, formatting your drive and then reinstalling win7 from scratch.

---

### Post by ubun2geek on 2011-09-04
What do you expect - it's windows!
I have to keep a windows pc around, and it takes 10 minutes to boot! (ubuntu is less than 10 seconds)
'nuff said. I'd go for ubuntu any day.
I hope I am not distro bashing.

---

### Post by BrokenKingpin on 2011-09-06
If you need a Windows installation on your laptop then I would just format it and reinstall Win7 fresh. Windows update should get most of the drivers, if not the laptop manufacturer should have the rest. 

I found the same thing with my Win7 install (maybe not a 5 minute boot, but getting longer and longer). I also found the shutdowns were taking longer and longer. Eventually I just deleted the partition and now running Ubuntu or Debian on all my machines... things are a lot better now :).

---

### Post by Dr. C on 2011-09-06
> **Ieroglif said:**
> Hi there,
  Sony VAIO VPCS11C5E
  Intel(R) Core™ i7 CPU         M 620 @ 2.67 GHz
  6 GB of RAM, 64-bit Operating system
  My computer is about 1,5 years old and suddenly won't start Windows 7 Professional or only starts it after about 5 minutes of loading.  I've run through several attempts to solve this problem and here are some of the results I get:
  -         The system restore cannot solve this problem
  -         It can’t sort it by returning to the earlier date (the date when it worked fine)
  -         The tests say that there are errors in Windows Device Manager
  -         USB and Surface Scan Tests failed (E-USB-001 & E-HDD-004)
  I wonder if it could happen while I was going through security X-Ray at the airport with my laptop in sleep mode?
  Also the computer now is operating slower than usual.
  Is this Windows 7 problem or is it my laptop? What can be done?
  Thanks,
  Irina

My first suggestion here is boot the laptop from an Ubuntu live CD to check if all the hardware works with Ubuntu. The failed USB and Surface Scan tests seem to point to failing hardware, so if you can get to to boot an Ubuntu live CD I would also use it to back up your data. 

If all the hardware works perfectly under Ubuntu then I would back up al your data and reinstall Windows 7.

5 min to boot up on those specs is excessive for Windows 7.

---

### Post by _d_ on 2011-09-06
Interesting. Your laptop specs beat my desktop specs:

HP Pavilion p6610f
AMD Athlon II x4 635 2.9GHz
4GB DDR3 RAM
Windows 7 Home Premium x64

And here is my boot time via BootRacer:

[IMG]http://i56.tinypic.com/16kvrlv.png[/IMG]

I'm suspecting you have some faulty hardware somewhere, or you have an absolute TON of programs that need to be started on boot.

---

### Post by JonM33 on 2011-09-09
> **jefelex said:**
> Why are you asking that here?  The whole point of Ubuntu is to completely replace Windows.  You say your computer is 1½ years old, it should run 11.04 with no problems at all - and boot in less than 30 seconds. 

Windows has seen it's day - it is old and bloated software, and not worth the kind of money they are asking for it.

Not sure how Windows 7 is old. That's like saying a 2 year old car is old and you should just throw it away.

What if he is having hard drive errors that are indicative of a hardware problem? Ubuntu isn't going to fix that.

---

### Post by amjjawad on 2011-09-14
> **Ieroglif said:**
> Hi there,
  [B]Sony VAIO VPCS11C5E
  Intel(R) Core™ i7 CPU         M 620 @ 2.67 GHz
  6 GB of RAM, 64-bit Operating system[/B]
  My computer is about 1,5 years old and suddenly won't start Windows 7 Professional or only starts it after about 5 minutes of loading.  I've run through several attempts to solve this problem and here are some of the results I get:
  -         The system restore cannot solve this problem
  -         It can’t sort it by returning to the earlier date (the date when it worked fine)
  -         The tests say that there are errors in Windows Device Manager
  -         USB and Surface Scan Tests failed (E-USB-001 & E-HDD-004)
  I wonder if it could happen while I was going through security X-Ray at the airport with my laptop in sleep mode?
  Also the computer now is operating slower than usual.
  Is this Windows 7 problem or is it my laptop? What can be done?
  Thanks,
  Irina


One way to tell: Give Linux a Try, period.

You can, for example, download Ubuntu (or any other Linux Distribution with LiveCD feature - most of them have it) and create a LiveUSB (faster than LiveCD) and boot your machine from that USB.
If you get the same response then your Laptop might have some issues and I doubt that.
If the response be better (I'm sure it will) then what are you waiting for? get rid of Windows ;)
Of course backup everything before doing anything. Either way, better safe than sorry. I mean whether your hardware is falling or Windows is saying good-bye, you better backup your "important files".

Good luck!

---

### Post by coffeecat on 2011-09-14
The OP has not been back since posting, so it's possible that all this advice is not being heard. :wink:

@Ieroglif, if you read this, you would be better off asking your question on a Windows forum anyway.

Thank you for participating, everyone.

Thread closed.

---

