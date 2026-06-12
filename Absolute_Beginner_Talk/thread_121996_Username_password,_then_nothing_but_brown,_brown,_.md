---
title: "Username password, then nothing but brown, brown, brown"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Happy Dave on 2006-01-26
Hi

I've just installed 5.10 for the first time on an old G3 500MHz IMac (Turqouise and White).  It took me several attempts, and I had to reburn the ISO image at progressively lower speeds before it got all the way through to finishing the install, as it kept erroring out during the core package install and later in the additional packages.  Finally, it was all done, ready to rock, so I booted it, got the lovely Ubuntu login screen and everything.  I entered my username and password and hit return, got the desktop startup sound I'm familiar with from using the Live CD and then....

Nothing but a brown screen.  I've tried all the different sessions, and the only one that works is booting to a default terminal, where I get a white rectangle in the bottom right of the brown screen with dave@ubuntu:~$ in the corner.  I'm a total, total n00b with both Ubuntu, Linux generally and command line use, so I have no idea what to do, or change or re-install.  I have an idea from reading various threads that it might have something to do with my video hardware?  Anyway, to restate, it's a standard G3 iMac 500MHz, which I've hosed so it's only booting Linux now.  Help please!

And please go easy, I'm new!

Oh, p.s.  I got the 5.10 DVD off the front of Linux Magazine this month and thought I'd try reinstalling from that, but it just spits it out (I guess it's a PC only version?)

Thanks!!

---

### Post by Koobi on 2006-01-26
it does sound like a video problem...


try going to the terminal via Ctrl+Alt+(F1-F6) and typing this:
```

lspci

```

check if your video hardware really IS standard.
to get out of terminal, hit ctrl+alt+F7

---

### Post by Happy Dave on 2006-01-26
Okaayyy, done, I have the following:

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 RL/VR AGP

Then I have stuff about the Host Bridge, Ethernet, USB controllers and so on, but I reckon it's the Display controller we're interested in, no?

What I don't understand is it displays the Login screen fine, but then just goes to brown.  Surely if one displays okay, the rest should?

---

### Post by Koobi on 2006-01-26
if i'm not mistaken, i think ATI cards have an issue with Ubuntu.

have you tried searching the forums for threads similar to this?

sorry i can't be of more help. i'm not too good with this sort of thing.

---

### Post by Happy Dave on 2006-01-26
I've had a look around, but I can't find anything specific - does anyone else have any ideas?

---

### Post by Happy Dave on 2006-01-26
After further investigation, it's my system clock.  Any other n00bs facing this problem should have a look here:

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by Mustard on 2006-01-26
Well done in finding the solution and even more so in coming back and posting that solution. :)

---

