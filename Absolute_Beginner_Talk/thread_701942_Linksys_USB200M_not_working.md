---
title: "Linksys USB200M not working"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by CyberDean on 2008-02-19
I now have my Gateway Solo 5150 running Ubuntu Linux 6.06 i386 for PC.  Not that it was easy or smooth and I still have bugs and devices that don't work and I am going to work on one at a time.

First up, my internet connection.  I have two possibilities.  The first is a Linksys USB200M, worked without any changes when I was trying Ubuntu 7.10.  Seeing I don't have internet at this time, can I retreive the proper software from a 7.10 alternate CD?

And the second possibility is a wireless linksys notebook adaptor, but I wish to try the USB200M first.

USB200M worked with 7.10, does not work with 6.06, the only thing on is the F/H indicator.  Had to down grade Ubuntu due to the laptop.

Anyone got any suggestions?  I had found the "Hardware list" at one time, but can not find now.

Thanks in advance.

Ok, I'm back after hours of researching this problem and not finding the solution.

I have just loaded the Ubuntu Linux 7.10 live CD onto my laptop, opened Firefox on the laptop with the Linksys USB200M network device, and am typing this message on the same laptop. Yes, it works on the internet.

I know I am new to Linux, but if this device works on this laptop using the 7.10 live CD and if I can find someone with more Linux knowledge than I, which wont be difficult, maybe we can find what is in Linux 7.10 than enables this device to work.

Contact me, I am sitting here with no where to go, it is snowing, schools have be closed, no youth meeting tonight, I'm just sitting here waiting. I have found many people having the same problem all over the internet and on this forum, just think of how many this can help.

I need some guidelines as to where to look, the proper commands, etc. And I still have the same question, can the proper install files be used from Ubuntu Linux 7.10 live CD to fix the USB200M problem in 6.06 Desktop installation? If so, how? If not, I'll have to find another way to get 6.06 on the internet.

Ok, I wont beg any more, and thanks for reading.
__________________

---

### Post by Jewfro_Macabbi on 2008-02-19
I'd guess the problem is the older version doesn't have the necessary kernel modules for that modem. It's possible upgrading your kernel version would fix that - or check the manufacturer's web site - There's a shell script about for install some Franklin Wireless usb modems - not sure about your manufacturer.

---

### Post by CyberDean on 2008-02-20
Ok, I'm back after hours of researching this problem and not finding the solution.

I have just loaded the Ubuntu Linux 7.10 live CD onto my laptop, opened Firefox on the laptop with the Linksys USB200M network device, and am typing this message on the same laptop.  Yes, it works on the internet.

I know I am new to Linux, but if this device works on this laptop using the 7.10 live CD and if I can find someone with more Linux knowledge than I, which wont be difficult, maybe we can find what is in Linux 7.10 than enables this device to work.

Contact me, I am sitting here with no where to go, it is snowing, schools have be closed, no youth meeting tonight, I'm just sitting here waiting.  I have found many people having the same problem all over the internet and on this forum, just think of how many this can help.

I need some guidelines as to where to look, the proper commands, etc.  And I still have the same question, can the proper install files be used from Ubuntu Linux 7.10 live CD to fix the USB200M problem in 6.06 Desktop installation? If so, how?  If not, I'll have to find another way to get 6.06 on the internet.:confused:

Ok, I wont beg any more, and thanks for reading.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Update:  When Ubuntu Linux 7.10 live CD is loading, at the time it loads the "Hardware Driver" package, the USB200M goes active.  Does anyone know what hardware package is loaded for 7.10 during bootup of the live CD?  Thanks

---

### Post by Jewfro_Macabbi on 2008-02-20
First question,

Why do think you need to use 6.06 on the laptop? 7.10 shouldn't consume any additional resources. I can tell from your description - the stock kernel in 6.06 doesn't have the module for that modem. It's possible that upgrading the kernel would fix it. Or it's possible you could install that module - maybe using "module-assistant" - which is hard when it has no net - maybe network it and update.

Really you could just install 7.10 - or if you want something lighter try the xubuntu 7.10 - xfce is a more lightweight desktop environment than gnome.

---

### Post by CyberDean on 2008-02-20
Thanks for the thoughts.  I was informed that the laptop did not sufficient memory to run 7.10.  I checked the Ubuntu site info and found a writeup that stated that, if I remember correctly, it needed 384MB of mem, mine has only 288MB.  6.06 requires less than 288MB.  But I am attempting to load 7.10 at this time again.  Time will tell.  If the Ubuntu 7.10 does not install, I'll try the Xubuntu 7.10.  Thanks again.

---

