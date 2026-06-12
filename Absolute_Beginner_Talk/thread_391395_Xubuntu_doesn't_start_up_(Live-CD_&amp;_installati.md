---
title: "Xubuntu doesn't start up (Live-CD &amp; installation)"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by mh789 on 2007-03-23
Hi!

I can't get Xubuntu starting. 

I tried starting the live-CD (6.10) on an old computer, but all I saw was Desktop and Login Screen switching back and forth every 5 seconds.

Then, I installed Xubuntu with the Alternate CD. Here the same. After logging in, I can see the Desktop for about 5 seconds, then it switches back to the login screen (but it does not switch forth to the Desktop as it waits for my password).

Any help appreciated

---

### Post by lyceum on 2007-03-23
What are your stats? Hard drive, CPU, RAM? If they are too small, it will not work. That is the first thing, as it is the easiest. :)

---

### Post by mh789 on 2007-03-24
Intel Celeron 400 MHz
192 MB RAM
HDD: some GB free

It seems to me that there's a programm that crashes the session, so that Xubuntu falls back to the login screen.

---

### Post by lyceum on 2007-03-25
You do not have enough RAM. For the live CD to run you need at least 256 MB. I can get a PC to run with less from time-to-time, but mostly no. If you want to wipe your hard drive and just run Xubuntu, you can with the alt install. Very easy. If you just want to check it out, I would say beef up your RAM just a little bit.

---

### Post by halitech on 2007-03-25
the main part of the system looks fine cause I'm running Xubuntu on 2 systems that are even lower (1 AMD K6-2/300 with 128 meg of ram, 4gig drive and 2. PII with 256meg RAM and a 6gig drive) and 6.06 runs fine. What do you have for a video card? I'm wondering if it's a video driver issue.

---

### Post by lyceum on 2007-03-25
> **halitech said:**
> the main part of the system looks fine cause I'm running Xubuntu on 2 systems that are even lower (1 AMD K6-2/300 with 128 meg of ram, 4gig drive and 2. PII with 256meg RAM and a 6gig drive) and 6.06 runs fine. What do you have for a video card? I'm wondering if it's a video driver issue.

You could be right, and yes his stats are fine for running Xubuntu on the hard drive, but they are not enough to run the live CD (which is odd, as you need a better PC to test it out that to run it.)

I just loaded Xubuntu on a couple of Pentium II PC's. One had 192 mb of ram, the other had 128. I had to use the alt install disk on both, and they ran fine. However, the the Live CD would not work on either. It would just load forever. Both were very fast with Xubuntu, way faster than they had been on XP/Windows 98. If you are looking at trying to bring older PC back to life, Xubuntu is the way to go.

---

### Post by halitech on 2007-03-25
> You could be right, and yes his stats are fine for running Xubuntu on the hard drive, but they are not enough to run the live CD (which is odd, as you need a better PC to test it out that to run it.)

most people have better then PII's anyway so not normally a problem

> 
I just loaded Xubuntu on a couple of Pentium II PC's. One had 192 mb of ram, the other had 128. I had to use the alt install disk on both, and they ran fine. However, the the Live CD would not work on either. It would just load forever. Both were very fast with Xubuntu, way faster than they had been on XP/Windows 98. If you are looking at trying to bring older PC back to life, Xubuntu is the way to go.

same here but I knew I was installing so didn't even try to run the live cd, went right to the alt cds cause I started with 128 on both and then upgraded the ram. Any lower then 128 though and I'd suggest DSL or Puppy.

---

### Post by lyceum on 2007-03-26
> **halitech said:**
> same here but I knew I was installing so didn't even try to run the live cd, went right to the alt cds cause I started with 128 on both and then upgraded the ram. Any lower then 128 though and I'd suggest DSL or Puppy.

Have you tried [Fluxbuntu](http://fluxbuntu.org/) yet? I am not sure how low you can go on the RAM, but I know it is lower than Xubuntu. I would not recommend it for new users though. It is fun, still in beta. The Alpha is going to release with Feisty.

---

### Post by mh789 on 2007-03-27
> You do not have enough RAM. For the live CD to run you need at least 256 MB.
Why do you think so? [http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu) states:
> CDs require 128MB RAM to run, or 192MB RAM to install. Desktop install requires at least 1.5GB of free space on your hard disk.

> If you want to wipe your hard drive and just run Xubuntu, you can with the alt install. Very easy.
Yes, I already did so (not wiping my hard drive though). It's not "very easy" As I wrote in my original post:
> I installed Xubuntu with the Alternate CD. Here the same. After logging in, I can see the Desktop for about 5 seconds, then it switches back to the login screen


> What do you have for a video card? I'm wondering if it's a video driver issue. Banshee.

I found a thread with the same problem: [http://www.ubuntuforums.org/showthread.php?t=392362](http://www.ubuntuforums.org/showthread.php?t=392362), but the solution there "noapic apci=off" did not work for me.

---

### Post by lyceum on 2007-03-27
I would say that I say the Live CD needs 256mb because it does. I have been able to get a PC to start from it from time to time with less, but it runs too slow if it starts up at all. If you were using the alt CD and it is now loaded then my guess would be the video card. I do not know enough about those. Can you load in text mode? This would just be a terminal. I do know you would need to be able to at least do that to fix what ever is not working. Sorry I could not be more help.

---

### Post by dstew on 2007-03-27
It might be an interrupt controller issue. The boot options are:

noapic nolapic

I am not sure about "apci=off". That one doesn't seem right to me. It turns off power management. But, sometimes you just have to try various boot options.

Also, when the kernel boots, it keeps a log file, and sometimes there are error messages that can help solve problems like this. I think it is in the /var/logs directory. See:

[http://ubuntuforums.org/archive/index.php/t-10508.html](http://ubuntuforums.org/archive/index.php/t-10508.html)

The command **dmesg** will show some of the recent dialog.

---

