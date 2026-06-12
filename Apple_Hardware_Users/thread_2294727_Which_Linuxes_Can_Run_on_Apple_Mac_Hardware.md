---
title: "Which Linuxes Can Run on Apple Mac Hardware?"
date: 2015-09-12
forum: Apple Hardware Users
---

### Post by yoshii on 2015-09-12
Hello, I was wondering which Linuxes can run on Apple Mac hardwares?  
I remember trying an earlier version of WattOS and I was surprised that it worked.  But my Puppy Linuxes wouldn't work on Mac.  
Does anybody know which ones work?  Or if my question is wrong, what info am I missing?  
I'm particularly interested in LiveCD's.  

Thanks in advance.  
Long live Linux!

---

### Post by QIII on 2015-09-12
*Moved to **Apple Hardware Users***

---

### Post by Mike_Walsh on 2015-09-12
Hi, yoshi2. Greetings from one 'Puppian' to another!

Have you tried MacPup? I think it runs on a Mac.....although in fact, as I recall, you can run any Pup on a Mac. Got to be done with Unetbootin, as far as I'm aware. Don't think it'll work as a LiveCD (mainly due to the fact that Macs haven't had optical drives for years.....unless you're talking about a real old one..!)

There's a link here that explains how you can actually run Puppy inside OS X (I don't know if that's of any interest to you):-

[http://www.co-bw.com/DMS_OS_running_puppy_linux_inside_OSX.htm](http://www.co-bw.com/DMS_OS_running_puppy_linux_inside_OSX.htm)

And if I'm correct, you can install most of the 'buntus, too. But again, I'm not certain if you can simply run a LiveCD; Macs are somewhat quirky, when it comes to anything 'non-Mac', as I'm sure you're aware!

What Mac are we talking about, here?


Regards,

Mike. ;)

---

### Post by yoshii on 2015-09-13
I'm not even sure which model of Mac it is.  it's got a huge screen and the computer is built into the monitor.  It has a CD/DVD drive on the right side of the monitor.  My mom purchased it a few years ago new.  It's a desktop model.  I am interested specifically in LiveCD's because I can't change too much on her computer without risking messing it up.  She lets me use it, but I don't want to change much of anything.  But once it crashed and I was still able to run WattOS on it via LiveCD... that's what got my attention with it.  And then I noticed some cheap used Macs for sale on CraigsList and I thought it might be fun to run Linux on them maybe.

---

### Post by OlafO on 2015-09-14
@yoshi2, most 'older' Macs like your mom's should be able to run most linuxes, but you may have to edit the boot parameters, like I do.

I have a 2009 MacBook Pro (5,2), and I'm able to run Live DVD (or Live USB Flash that I'd recommend, since it's a LOT faster than DVD) of the following:
1. Ubuntu 14.04.3
2. Linux Mint MATE 17.2 (The Cinnamon version complains about running in software emulated mode & MATE doesn't, plus MATE looks more 'Mac-like' IMO)
3. Xubuntu 14.04.3
4. Linux Mint Xfce 17.2

The only caveat is that once each of these get to the grub2 boot screen, I had to hit the 'e' key and edit the part of the kernel options that have "quiet splash" and replace with "nomodeset", hit fn+F10. The reason I have to do this is that my Mac has the nvidia 9600 video hardware, and most recent linux kernels don't deal well with it, hence the required "nomodeset" option. YMMV (your mileage may vary)

OlafO

P.S. The 'newest' Ubuntu Live DVD that runs without any issues (i.e., manual boot parameter edits) on my Mac is version 10.04.4, which is quite dated at this point.

---

### Post by yoshii on 2015-09-14
Thanks so much for your consultation.

---

