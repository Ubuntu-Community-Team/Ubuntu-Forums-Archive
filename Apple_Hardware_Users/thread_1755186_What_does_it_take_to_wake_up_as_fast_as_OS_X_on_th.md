---
title: "What does it take to wake up as fast as OS X on the Macbook air?"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by franciscohs on 2011-05-10
Ok, so, I bought the macbook air mainly for the hardware, and used OS X for a week to try it out and in the end, I figured it wasn't really for me, there are a lot of things I just can't get used to, I guess I'm simply a Linux guy, so I installed Ubuntu and it works great.

However, I REALLY miss how fast OS X wakes up on the Macbook air with OS X, and specially, how the wireless is on as soon as I finished opening the lid, it must be in a second or 2 at most that the computer is ready to use and connected.

It takes almost 25 seconds on ubuntu to go to the desktop and about 25 more seconds to get connected. The difference is really noticeable, I was wondering if anyone knows what it takes to reduce this time and if it's (at least theoretically) possible to take these times WAY down, to a few seconds at most, to be comparable to OS X. If it's not possible, do you know how it's done in OS X?

---

### Post by tgalati4 on 2011-05-11
My 6-year old powerbook wakes in 3 seconds under Tiger.  My 4-year old thinkpad wakes in 15 seconds under Jaunty.  

Go through the wake scripts and you will see why it takes so long.  Apple OS is optimized for Apple hardware.

Ubuntu is optimized for?

---

### Post by v41 on 2011-05-11
It shouldn't take nearly that long.  To find out what's taking the time, open a terminal and issue the following command,> dmesg | grep msec

On my Mac (macbook-4.1, Ubuntu 10.04), resume-from-suspend is very quick (a couple of seconds) the first couple of times after a fresh boot.  But on the third or fourth resume, the time increases by 10 seconds.  Using the above command, I found that the battery is taking 10 seconds to resume.  Unfortunately I don't have any solution for this )-:

---

### Post by franciscohs on 2011-05-11
> **v41 said:**
> It shouldn't take nearly that long.  To find out what's taking the time, open a terminal and issue the following command,

On my Mac (macbook-4.1, Ubuntu 10.04), resume-from-suspend is very quick (a couple of seconds) the first couple of times after a fresh boot.  But on the third or fourth resume, the time increases by 10 seconds.  Using the above command, I found that the battery is taking 10 seconds to resume.  Unfortunately I don't have any solution for this )-:

That's interesting, in my case I'm too seeing that the battery takes about 10 seconds to resume, my nvidia card is second with almost 5 secs. It also varies a lot, I have another suspend that took almost 4 secs for the USB dev when normaly it takes only about 200msec.

This explains part of the "problem", what about the wireless access?, it would seem that OS X resumes the wireless session as it left off without the need to reconnect or anything. Is this so?, it is possible to do something like that on Ubuntu?

@tgalati4: I know that, and with my comment I'm not bashing ubuntu but prising the ability of os x + mac hardware to do so. I was just wondering is with optimization it could be possible to do with Ubuntu or because of the architecture or whatever, it's probably just not possible.

---

### Post by v41 on 2011-05-11
> **franciscohs said:**
> ...what about the wireless access?, it would seem that OS X resumes the wireless session as it left off without the need to reconnect or anything. Is this so?, it is possible to do something like that on Ubuntu? ...

Hmmm... my wireless (broadcom BCM 4328 also takes a while to resume under Ubuntu, around 15 seconds.  There is a[ thread about the long resume time]("http://ubuntuforums.org/showthread.php?p=9360872"), a related [bug report,]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405") and [another bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/620318").  There are various possible workarounds mentioned but I haven't tried them.  Incidentally, the "hardinfo" package gives details about your computer's hardware, including the wireless card.

---

### Post by franciscohs on 2011-05-12
> **v41 said:**
> Hmmm... my wireless (broadcom BCM 4328 also takes a while to resume under Ubuntu, around 15 seconds.  There is a[ thread about the long resume time]("http://ubuntuforums.org/showthread.php?p=9360872"), a related [bug report,]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405") and [another bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/620318").  There are various possible workarounds mentioned but I haven't tried them.  Incidentally, the "hardinfo" package gives details about your computer's hardware, including the wireless card.

I'll take a look. Thanks.

BTW, the battery wakeup problem seems to be solved by adding "acpi=rsdt" to the kernel line in grub. So far is working for me, although some people claim it works for the first suspends and then it goes back to 10secs or more..

Now the only thing that is delaying the resume is my nvidia driver (around 5secs), I didn't find a solution to that.

---

### Post by tgalati4 on 2011-05-21
You are doing precisely what Apple engineers did a few years ago--finding the delays and rewriting the drivers to reduce the delays.  That is how you get snappy performance.  With Ubuntu, you can tweak and tweak and ultimately run into a proprietary driver (binary blob) that you have no control over.

Apple knows this and will do anything to prevent opening up hardware drivers.  It's one of their trade-secrets and something that distinguishes their brand and lock-in philosophy.

---

