---
title: "Linux on flash drive"
date: 2010-01-29
forum: Apple Hardware Users
---

### Post by deweyo on 2010-01-29
Hello - I'm a newbi so bear with me. I'm using a G4 Ti powerbook that I got used because It's allI can afford right now (daughters in college). I've used Macs & PC's right along and the Mac wins hands down. The problem is in my trade (automotive) there are programs that I need to use that are only written for PC's. Some will run on Virtual PC for me but the most important one will not - the program will run but the data coming in via USB experiences "too many communication errors to continue". There is documentation that many users have had great success running this program on Linux so in lieu of buying a PC laptop just for this one program I thought about the possibility of adding Linux to this G4 laptop. I would like to keep everything as it is and add Linux to my drive. I have about 4g left which is not very much in this day & age so have been considering getting an external drive or maybe a large flash drive. Can this be done - install and boot Linux from a flash drive , install and run this small app on the same flash drive and finally connect thru the other USB port to the car?

Dewey

---

### Post by djchandler on 2010-01-29
If you want to use Linux to run the Windows compatibility layer, start here:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

We also have a Mac specific forum:

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Since you are running on a G4 PPC CPU, what you are wanting is not an easy accomplishment in this case. If you had an Intel Mac, you possibly wouldn't even need Linux and could run Win32 EXEs using a compatibility layer called [Wine]("http://wiki.winehq.org/MacOSX") in OS X itself.

The problem is the G4 is not instruction set compatible with Intel or AMD x86 or x64 CPUs, and requires an emulator in order to run. You might be better off using a program called an emulator to run your software, but even then there's no guarantee your software will work due to the necessity to communicate with proprietary hardware via USB. I would imagine this is exactly what you are running into using Virtual PC and all the communication errors you are experiencing. Timing is probably the issue due to the latency introduced by the necessity of translating CPU instructions.

As cheap as a Pentium 4 can be bought right now (if you know where to look), if I was in this situation I would be locating actual Intel or AMD CPU based hardware for your automotive application. I had a Dell Pentium 4 in my hands just today that cost $20 at our local surplus/recycling center with no hard drive or memory. Easily you can get an entire working system for around $100 dollars including monitor, keyboard and mouse. Linux is free,  and so is the WINE compatibility layer software.

But here's a few things you may try before resorting to obtaining more hardware in addition to the link at the top of my response. Try this link:

[http://www.macwindows.com/emulator.html#PCEmulators](http://www.macwindows.com/emulator.html#PCEmulators)

This is the free one:

[http://bochs.sourceforge.net/getcurrent.html](http://bochs.sourceforge.net/getcurrent.html)

---

### Post by deweyo on 2010-01-30
Thanks - at least I now know where I stand. Finding a system as  inexpensive as the one you mentioned is non-existent where I live (rural northeast). There are no, I repeat, no such things as recycled notebooks here. People must just stuff them in a closet or something. Too fearful of someone getting their information I suppose. Combine that with the fact that I really hate Windows in all it's infected glory I'm going to have to resign myself to sucking it up and buying one just for the one program because the price of an Intel Mac is out of the question.

All in all I again thank you for pointing me in the direction I need to go.

Dewey

---

### Post by djchandler on 2010-01-30
Have you tried eBay or another such option?

[Here's a local Kansas City company]("http://www.laptopsquad.com/") that takes laptops from business leases and recycles hardware they do stand behind, as well as warranty transfers. As mail order for a used laptop looks like your only option as opposed to a new computer, you may want to give these folks a try first. If you have problems, I'll be glad to go down there and yell at them for you!

No, seriously, I know several knowledgeable people who use [Laptop Squad]("http://www.laptopsquad.com/"), especially for running Linux.

Also, are you aware of the [OSx86 Project]("http://www.osx86project.org/")? These people know how to run vanilla, i.e., unaltered OS X on a lot of different hardware. They can steer you to a model that you can do this with. I am not advocating violating the cumbersome Apple OS X End User License Agreement, just making you aware that this is possible.

---

