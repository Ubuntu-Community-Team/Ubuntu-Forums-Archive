---
title: "Spontaneous Reboot?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-05-15
I am having issues with my PC spontaneously rebooting.  I can't figure out what causes it although I know it is not a tempurature issue.  Sometimes it happens many times in a row and sometimes it goes for hours without rebooting.

I built this computer from scratch (my hubby is saying "I told you!") and it is my first build.  Could it be a power supply issue?  I got a Compusa brand 400W power supply.  I'm on a budget and didn't want to spend a lot more.

Or is this related to my operating system?  (Feisty Fawn)

Also, is there a good beginner's guide to Ubuntu?  I'm looking for a sort of light read (like a "For Dummies" type book).  I don't want to read a manual.  I'm very new to Linux!

---

### Post by smoker on 2007-05-15
have you done a memtest on your ram, could be faulty ram, and if you haven't got a power supply to swap out and try, then try disconnecting power to all but your motherboard, graphics, and hard drive, and see if the problem goes, if so reconnect, eg, cd drives, other hard drives, usb power devices, until (or if) the restarts begin again.

---

### Post by Benbow on 2007-05-15
Sorry I can't help with your problem but on recommendation I bought "Ubuntu Linux for non geeks" by Rickford Grant. I have, together with this forum, found it a great help as it guides you through Ubuntu in chatty, easy steps.
I got it from Amazon UK but I should think that it would be available wherever you are.
Hope this helps.

---

### Post by lazyart on 2007-05-15
Congrats on building your first machine.

Rebooting like you described is usually related to heat, faulty power supply or bad memory.  Many motherboards nowadays have voltage meters in their BIOS setup.  If your PS is dropping significantly below 12.00 or 5.00 volts (depending on the rail) you might have problems.  Does your motherboard have the additional 4 prong power receptacle?  Is the PS plugged into it?

Memtest is a good way to check your memory.  Google that, put it on a disk and boot from it and let it run overnight.

---

### Post by bean77 on 2007-06-18
> **lazyart said:**
> Congrats on building your first machine.

Rebooting like you described is usually related to heat, faulty power supply or bad memory.  Many motherboards nowadays have voltage meters in their BIOS setup.  If your PS is dropping significantly below 12.00 or 5.00 volts (depending on the rail) you might have problems.  Does your motherboard have the additional 4 prong power receptacle?  Is the PS plugged into it?

Memtest is a good way to check your memory.  Google that, put it on a disk and boot from it and let it run overnight.

The motherboard DOES have the 4-prong power receptacle and it is plugged in.

I'll check the memtest.

I hope I can fix this!

---

### Post by bean77 on 2007-06-18
```
lydia@lydia-desktop:~$ memtest
memtest v. 2.93.1
(C) 2000 Charles Cazabon <memtest@discworld.dyndns.org>
Original v.1 (C) 1999 Simon Kirby <sim@stormix.com> <sim@neato.org>


Copyright (C) 1999 Simon Kirby.  Version 2 Copyright (C) 2000 Charles Cazabon.
This is FREE SOFTWARE, licensed under the GNU General Public License version 2.
See the included file COPYING for details.  This software comes with absolutely
NO WARRANTY.

Usage:

memtest <mem<B|K|M|G>> [runs] [-l or --log]
    mem          - memory to test (B=bytes, K=KiB, M=MiB, G=GiB)
                   Byte values will be rounded down to nearest multiple of 64.
                     e.g. 2G   =  2 GiB
                          12M  = 12 MiB
                   Special value 'all' tests all available memory.
    runs         - times to run tests (default: 2^32 - 1)
    -l or --log  - log to file memtest.log
```

Does this make any sense?

---

### Post by hardyn on 2007-06-18
run memtest from the live disk or the grub prompt

spontaneous reboots are often trouble in the motherboard, make sure the ram is seated, make sure the socket is clean.  unfortunately a bad motherboard isn't all that uncommon; i have scrapped a few for that symptom.

were there any jumper configurations?
how do you know its not heat related?
correct speed ram?
is the processor supported in that firmware version?

---

### Post by bean77 on 2007-06-19
went inti BIOS, my system fan speed is 0, my cpu fan speed is 2596 rpm...is this the issue?

---

### Post by w4ett on 2007-06-19
If you run Memtest and it passes and all your connections and cables are fully inserted and properly seated in the sockets, try resetting your bios to the default settings (slowest bus, memory speed) and reboot...see if this helps.

---

### Post by hardyn on 2007-06-19
the fan is spinning, but that does not mean that it is conducting heat well:
what is the temperature of the CPU under operation?

---

### Post by bean77 on 2007-06-19
> **hardyn said:**
> the fan is spinning, but that does not mean that it is conducting heat well:
what is the temperature of the CPU under operation?

system temp is 34c/93f

CPU temp is 56c/132f

---

### Post by hardyn on 2007-06-20
not abnormal
how did the memtest work out?
barring that return/warranty the motherboard.

---

### Post by bvanga on 2007-06-20
I had the same spontaneous rebooting for mine too... but then again it could be different from yours too. I did memtest, unplug and replug everything, I even try install different os and it still did the same thing. I did everything I could think of.  So I just replaced my 430w power supply unit, and it works fine. faulty power supply like mine maybe??

---

### Post by shields on 2007-06-25
Are you sure this is a reboot?  I am getting a "spontaneous restart", for lack of a better term.  

It's not a reboot because I never see any bios stuff -- just the login screen.

I posted more details here:[URL="http://ubuntuforums.org/showthread.php?p=2909747#post2909747"]
http://ubuntuforums.org/showthread.php?p=2909747#post2909747[/URL]

---

### Post by bean77 on 2007-07-09
> **shields said:**
> Are you sure this is a reboot?  I am getting a "spontaneous restart", for lack of a better term.  

It's not a reboot because I never see any bios stuff -- just the login screen.

I posted more details here:[URL="http://ubuntuforums.org/showthread.php?p=2909747#post2909747"]
http://ubuntuforums.org/showthread.php?p=2909747#post2909747[/URL]

It's like I hit the "reset" button.  Starts over from the very beginning, gives me the option to enter BIOs, etc., etc.

I switched out the power supply-not the issue.  Ran the memtest, no problems.

What now?

---

### Post by bean77 on 2007-07-09
With mbmon I am getting: 
```
lydia@lydia-desktop:~$ sudo mbmon
No Hardware Monitor found!!
InitMBInfo: Success

```

---

### Post by twiceasworn on 2007-07-09
How long have you had the machine?  Did these reboots just start happening?  If so, had you changed anything that could be causing it?

I am with everyone else pretty much.  Random reboots are either related to heat (which you seem to not have a problem with), motherboard, ram or power supply.

Does it reboot when it is just idling at the desktop, or do you have to put a load on it for it to happen?

---

### Post by bean77 on 2007-07-09
> **twiceasworn said:**
> How long have you had the machine?  Did these reboots just start happening?  If so, had you changed anything that could be causing it?

I am with everyone else pretty much.  Random reboots are either related to heat (which you seem to not have a problem with), motherboard, ram or power supply.

Does it reboot when it is just idling at the desktop, or do you have to put a load on it for it to happen?

I've had the machine since April and it's been doing it pretty much the whole time.  I am in contact with MSi, the motherboard manufacturerrs so hopefully they can send me a new one.

---

### Post by lou1998 on 2007-08-17
Just curious if you ever fixed your rebooting problem.  I am having the same issue.  I suffer from random reboots all the time (regardless of what I am doing, CPU load, etc) and occassionally, while playing WoW, the machine just freezes up.

---

### Post by bean77 on 2007-08-17
> **lou1998 said:**
> Just curious if you ever fixed your rebooting problem.  I am having the same issue.  I suffer from random reboots all the time (regardless of what I am doing, CPU load, etc) and occassionally, while playing WoW, the machine just freezes up.

It was a faulty motherboard.  I exchanged it for a new one.

---

### Post by bean77 on 2007-09-27
Argh-it's happening again even with the new motherboard.  I'll include a video of my boot up screen...ignore the kids playing in the background.

[http://www.youtube.com/watch?v=Xq2zwn-iAmo](http://www.youtube.com/watch?v=Xq2zwn-iAmo)

---

### Post by raydeen on 2007-12-05
I don't know if this is related or not, but I had my first spontaneous reboot tonight on my laptop running Gutsy. Never had it before but tonight I installed a program called PowerTOP to try to tame the battery hungry beast that is Gutsy. I was getting a bit low on power but not critical and in the middle of reading a web page, the computer just restarted. I'm thinking that some change that was made by PowerTOP caused the reboot but won't know till I test it further on battery power. I'm in Windows now typing this as Gutsy was still chewing through the remaining power even after the reccomended changes had been made. I hope Hardy is better on the battery then Gutsy.

---

