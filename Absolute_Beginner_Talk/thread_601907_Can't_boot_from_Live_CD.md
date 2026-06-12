---
title: "Can't boot from Live CD"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by 4x4lo8o on 2007-11-03
I've been trying to install Linux on an older Dell desktop a friend gave me. I've been unable to get it to boot from Linux Live CD's though.
When I try to boot from Ubuntu 7.10 Live CD the menu comes up fine, but after I chose Start or Install Ubuntu it'll get about 3/4's of the way through loading and then stop.

It's not a problem a with the CD. I've tried it on two other computers and it's worked without problems, as well as checking the CD for defects. The computer has 2 disc drives, one's a CD/DVD reader and writer and one just reads CD's, and I have the same problem trying to boot from either one. I also have an external USB disc drive I tried, but I can't get the BIOS to recognize it. 
I've also tried a couple of other Linux distro's, and had similar problems.

Anyone have any idea what my problem might be?

---

### Post by overdrank on 2007-11-03
> **4x4lo8o said:**
> I've been trying to install Linux on an older Dell desktop a friend gave me. I've been unable to get it to boot from Linux Live CD's though.
When I try to boot from Ubuntu 7.10 Live CD the menu comes up fine, but after I chose Start or Install Ubuntu it'll get about 3/4's of the way through loading and then stop.

It's not a problem a with the CD. I've tried it on two other computers and it's worked without problems, as well as checking the CD for defects. The computer has 2 disc drives, one's a CD/DVD reader and writer and one just reads CD's, and I have the same problem trying to boot from either one. I also have an external USB disc drive I tried, but I can't get the BIOS to recognize it. 
I've also tried a couple of other Linux distro's, and had similar problems.

Anyone have any idea what my problem might be?

HI  and welcome, you may Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
Also when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash so you can see any errors.

---

### Post by 4x4lo8o on 2007-11-03
I did a checksum and everything was fine. I've tried the CD on a couple of other computers and it's worked, so I'm pretty sure it's something wrong with my hardware. I just don't know what.

I tried pressing f6 and removing quiet splash and booting again. It kept going through a bunch of lines of stuff, it went pretty fast but I didn't see any errors. It finally just stopped at a line reading
"*Starting Common Unix Printing System : Cupsd"

---

### Post by SOULRiDER on 2007-11-04
How much RAM do you have? Have you tried checking your RAM with the Memory rest included in the Live Disc? I suggest you try installing with the Alternate disc instead of the live one.

---

### Post by 4x4lo8o on 2007-11-04
I've got 512mb of RAM, which I'd think would be enough. I'm running the memory test right now, but it looks like it's going to take awhile.

The alternate install is all text based, and I don't have much experience with command line. I'll give it a try, but is that going to give me problems?

---

### Post by SOULRiDER on 2007-11-04
Honestly its pretty much the same just the interface is different. Dont worry, youre not gonna ahve to do any typing or anything. If you have any problems installing just ask here!

---

### Post by 4x4lo8o on 2007-11-04
Does the memory test ever end? I let it run over night and it's still going, it look like it's repeating itself. It's not reporting any errors.


I'm burning the alternate install to a CD right now, so I'll be trying that shortly.

---

### Post by 4x4lo8o on 2007-11-04
I used to alternate install CD, it was pretty easy and everything seemed to install ok but then I ran into an interesting problem. It finished installing and I took the CD out and rebooted from the hard drive. It started loading and was at the same loading screen that you get with the Live CD, with ubuntu logo and a loading bar under it, and it stopped loading and just froze at the same place as it would when I tried booting from the Live CD.

I presume this means there's some problem or incompatibility with my hardware, but I don't have any idea how to resolve it or figure out what exactly the problem is. Any idea what I should try from here?

---

### Post by 4x4lo8o on 2007-11-06
Thought I'd bump this, try and get a reply, since I'm really stuck and have no idea what to try from here.

---

### Post by 4x4lo8o on 2007-11-07
One last bump before I give up on Linux for another 6 months or so and put Windows back on this PC. Eventually I'll get Linux working on one of my systems, but I guess it might not be this try

---

