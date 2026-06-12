---
title: "Finding out Hardware Problems"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by MuRRe on 2005-09-19
Hi!
So, i got myself a notebook some weeks ago. It's a Acer Aspire 5024.
I tried the ubuntu-5.10-preview-live-amd64.iso. I really like what i saw. So im going for Ubuntu, IF there is way to see what won't work before install. When I used the live CD my WiFi didn't work, neither did it recognize my battery.
My questions:
1. Is there any way to check if my hardware is compatible?
2. I have a Broadcom 802.11g WiFi-card. (if u want more info u have to tell me where i can get it).

The reason im switching are these:
I have 64-bit processor and want to use it.
It's also for educational purpose. I'm learning Java in school and we are using Unix alot in school. For me are an XP user it's a bit hard with the console.

I read some other threads, and the answer is:
Yes i want to sit and "copy/paste".  ](*,)  ](*,)  ](*,) 

Thanks

---

### Post by mlomker on 2005-09-19
> 
1. Is there any way to check if my hardware is compatible?


You could try searching Google for other people that have installed linux on your laptop.

> 
2. I have a Broadcom 802.11g WiFi-card. (if u want more info u have to tell me where i can get it).


Broadcom cards have to use ndiswrappers.  There are a number of [how-to's](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)  on here for setting that up. The amd64 version requires 64-bit Windows drivers...make sure they are available for your card if you go with amd64.

> 
The reason im switching are these:
I have 64-bit processor and want to use it.


Be aware that there are a number of key things that are not available on 64-bit, such as flash and a reliable java broswer plug-in.  Not to mention Realplayer and many other non-gpl application that you can't get source for.

---

### Post by MuRRe on 2005-09-20
Thanks for the answer. I i have 64-bit driver for the WiFi that is for Windows Vista.
So, Ndiswrapper uses a windows driver and converts it to linux?

---

### Post by mlomker on 2005-09-20
[QUOTE=MuRRe]Thanks for the answer. I i have 64-bit driver for the WiFi that is for Windows Vista.
So, Ndiswrapper uses a windows driver and converts it to linux?[/QUOTE]

Exactly and that driver should work.

---

### Post by MuRRe on 2005-09-20
Do that work for the other drivers to, like the driver for the processor and the touchpad?

---

### Post by mlomker on 2005-09-20
[QUOTE=MuRRe]Do that work for the other drivers to, like the driver for the processor and the touchpad?[/QUOTE]

No.  What makes you think you need a driver for those?  Linux supports touchpads.

---

### Post by MuRRe on 2005-09-20
Ok. SO the only problem is the Wifi then? what about the battery, how do i deal with that problem?
I will try to find out as much as possible myself, but i just the computer to work in school. Therefor i need the battery and Wifi...

---

### Post by mlomker on 2005-09-20
> much as possible myself, but i just the computer to work in school. Therefor i need the battery and Wifi...

I think you need to boot the liveCD and start answering some of these questions yourself.  Half of the things that you're concerned about have worked in linux for years.  

Perhaps you should play with Knoppix or other liveCD's for a while and wait to install it on your hard disk until you've figured some of these things out.  If you've never used linux before then I don't recommend installing it on a machine that 'has to work.'  It probably won't work well until you've spent some time learning how to use it and learn a bit about linux.

---

### Post by MuRRe on 2005-09-20
But Will have it besides Windows, so that I always have a way out if needed. But thanks anyway, for taking the time.
BTW i can't open [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by mlomker on 2005-09-20
> BTW i can't open [www.ubuntuguide.org](www.ubuntuguide.org)

Yeah, I saw that mentioned on a couple other threads as well.  They must have the site down for maintenance or something.

There's an [unofficial Kubuntu guide](http://kudos.berlios.de/kf/kf1.html) that is still reachable.  Not sure what you're looking for, though.  The [linuxquestions](http://www.linuxquestions.org) forum is also a decent site.  It's generic linux, though, and a lot of the posters seem to be advanced users.

---

