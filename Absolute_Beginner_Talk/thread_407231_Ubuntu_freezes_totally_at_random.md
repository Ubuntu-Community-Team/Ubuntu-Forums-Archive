---
title: "Ubuntu freezes totally at random"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-04-11
Hey guys, I'm not really sure how to get about troubleshooting this issue. 

Since less than 24 hours ago, my power supply unit was exchanged because the previous one died. When my previous psu died a few days ago, there were bios issues and I didn't realise it was such a huge problem until I tried loading into Ubuntu and WinXP. Then, the system would boot halfway into either of the o/ses and die. 

Okay, ever since I put in the new power supply unit, Ubuntu has been freezing totally at random. This means that there is no input from keyboard and thus, MAGIC keys don't work. (YUIB) As a result, I've been forced to do a cold reboot. 

When this problem of Ubuntu freezing completely started, I had not installed the latest updates yet as my pc was knocked out for a few days. After this problem started, I installed the latest updates but they've not fixed this issue. 

Also, I noticed something: On at least two occasions when the system froze, I was using Ephiphany or Swiftfox and I was typing within the browser. 

There's also something else and that is: right after installing the updates, the desktop kept restarting last night for me. 

(edit: oh yeah!!! I installed some new ATI drivers in order to hopefully solve this issue. " xorg-driver-fglrx " is the name. )

Man, is there any kinda command or utility that could help me? So far, from my system logs, there don't seem to be any messages that relate to this issue. If only Ubuntu was like WinXP and had plenty of troubleshooting programs. 

So, someone tell me please, installing a new power supply unit will NOT have any issues on an operating system, right? We had the system tested thoroughly and it was booted up at least 3 times with the new PSU installed. 

Also, could it be possible that when the system booted halfway into Ubuntu and died(full description at top of this message), could part of Ubuntu have been corrupted?

And finally, if I have xserver-xorg-video-ati and  xorg-driver-fglrx installed, what are my chances of having some system drivers conflict?

---

### Post by BarfBag on 2007-04-11
Dang.  A randomly freezing system with no error logs is a bad sign.  Why did you have to replace your power supply?  Was there a surge that knocked it out?  If so, it probably fried the motherboard was well.  That happened to me once.  I experienced the same problem you're having right before mine died.

---

### Post by Lucifiel on 2007-04-11
Hmmm... no, it was not a surge. It's just that Antec Truepower PSUs have had an issue of bad capacitors.

Edit: sites like johnnyguru.com and silentpcreview.com have covered this issue, before.

---

### Post by hardyn on 2007-04-11
If it is affecting both OSes... and now you are seening ramdom crash issues... its pretty likely you have wiped out some ram or a motherboard.

the caps are used to pull the ripples out of the power that has been knocked down by the transformers... you might have had some rippley power run though your machine, or a surge as the caps blew... a surge does not have come from outside to be deadly... a surge could have been generated from inside the PSU...

find a friend and start trading parts until you can figure out what has happened.

good luck.

---

### Post by Lucifiel on 2007-04-11
> **hardyn said:**
> If it is affecting both OSes... and now you are seening ramdom crash issues... its pretty likely you have wiped out some ram or a motherboard.

the caps are used to pull the ripples out of the power that has been knocked down by the transformers... you might have had some rippley power run though your machine, or a surge as the caps blew... a surge does not have come from outside to be deadly... a surge could have been generated from inside the PSU...

find a friend and start trading parts until you can figure out what has happened.

good luck.

Oh no, that was because the PSU died shortly after I tried to load in both the o/ses. 

Right now, there are no problems loading WinXP or Ubuntu. My problem is with Ubuntu freezing randomly. Hmmm... come to think of it, aren't Ephiphany and SwiftFox Mozilla builds? I'd better stay off them and try using Opera instead. 

After all, I've also seen kernel freezes related to Mozilla builds before.

Edit: And yeah, it's quite possible the rams might have been wiped out. Guess I'll try memtest86 then.

---

### Post by Lucifiel on 2007-04-11
Okay well, I think I'll test for software issues first.

1) I've uninstalled xserver-xorg-video-ati 

2) I'm now going to use browsers which are not built from Mozilla  .

We'll see how this goes. If there are any further issues, I'll move onto hardware testing. ;)

---

### Post by Lucifiel on 2007-04-13
Uninstalling xserver-xorg-video-ati  was a big mistake. I'd to enter Recovery mode and edit xorg.conf and select VESA drivers. 

So far, there has been 1 system freeze. 

I've run Memtest86+: not for the whole day but I selected Test 5 and let it run for 5 passes. Then, I selected Default test(all the tests) and let it run for 2 passes. No problems.

I'm now running > badblocks -vs /dev/hard disks and after which, I'll run Primetest and possibly, 3d mark 2000 on Windows.

Oh and cooling wise, my system is pretty okay.

I've got at one small fan located somewhere under one of my hard disks, a big 3d rocket II fan, and possibly a couple more fans located elsewhere.

---

### Post by Lucifiel on 2007-04-14
All right, I finally found the cause of this issue.

My new PSU also supports running in fanless mode and the fan must've been turned off, by mistake.

Anyways, before anyone starts freaking out about my cpu life, I've got the fan on my CPU, 1 huge fan(a 3d rocket II) in my computer, and another fan under my hard disks. Plus, my motherboard auto shuts down the cpu if it gets too hot. :p

---

