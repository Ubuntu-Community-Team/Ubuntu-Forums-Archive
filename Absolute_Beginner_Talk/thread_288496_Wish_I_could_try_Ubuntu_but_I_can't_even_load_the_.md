---
title: "Wish I could try Ubuntu but I can't even load the LiveCD"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by SillyClown on 2006-10-29
I have been itching to try Linux and decided to give it a go. Here is my system:

DFI Lanparty nForce 250Gb 
AMD Athlon 64 3000+
ATI x800 XL AGP vid card
2gigs RAM
(1) 120gig IDE Drive - Master  
(1) 80gig SATA Drive - Slave


Tried both 6.06 and 6.10 images burned according to the instructions (imgburn). Tried both builds for x86 and 64 bit architecture just for the heck of it. I have burned around 6 CD's of Ubuntu and get the same problem.  All I want to do is give it a test drive and see how the LiveCD works. 

Changed BIOS to boot from CD 
CD loads just fine and I choose option 1 to start/install 
   (a) in 6.06 I get to the loading Hardware Devices and it then does a reboot but I never get to a POST screen. The CD drive just continually spins up and down.
   (b) in 6.10 I see the Splash screen of Ubuntu with what appears to be a progress bar similar to that of XP loading up and then the same thing occurs. Machine does some sort of shutdown/reboot and it doesn't recover from it. It just sits there and never does the MoBo 'beep' and POST.

I've tried Knoppix LiveCD and that runs fine but no other Linux distro. I guess I could try some others but I'd really like to see what all the hoopla is with Ubuntu. Any help would be great.

Thanks in advance.
Chris

---

### Post by Snoopy381 on 2006-10-29
try the ubuntu alternate image, that way it wont load the graphical desktop untill after you have installed ubuntu. which by then all the correct drivers/settings should have loaded and you should have more chance of getting it to work.

---

### Post by Sef on 2006-10-29
You could order Dapper from [ShipIt]("https://shipit.ubuntu.com/").

---

### Post by SillyClown on 2006-10-29
> try the ubuntu alternate image, that way it wont load the graphical desktop untill after you have installed ubuntu. which by then all the correct drivers/settings should have loaded and you should have more chance of getting it to work.

If I do that then I defeat the purpose of trying it out before loading it to my hard drive. Oh well...after doing some more detailed searches I found a thread that an older release of Ubuntu had issues with x300-x1900 ATI cards. Everyone experienced the same thing I did. Only it could be fixed by getting to a console and typing in a sudo line of some sort. Not sure how I can get to a command line if I can't even boot up. Maybe I'll just wait until the next release to give Ubuntu a shot.

---

### Post by rccharles on 2006-10-29
> **SillyClown said:**
>  Not sure how I can get to a command line if I can't even boot up. Maybe I'll just wait until the next release to give Ubuntu a shot.

Wait until you feel Ubuntu has stopped installing/loading, then press control, alt, F1.  You may need to press these keys more than once.  This will bring you into the console.  

Robert

---

### Post by SillyClown on 2006-10-30
> Not sure how I can get to a command line if I can't even boot up. Maybe I'll just wait until the next release to give Ubuntu a shot.

See that's the thing...everything appears to be loading fine. As soon as I see "Loading Hardware Devices" it doesn't freeze up it just immediately reboots my machine but my monitor never flips back on. I don't even get to a post. My installation I guess doesn't 'freeze up' as some do mine just crashes.

---

### Post by coolbian57 on 2006-10-30
> **SillyClown said:**
> If I do that then I defeat the purpose of trying it out before loading it to my hard drive. Oh well...after doing some more detailed searches I found a thread that an older release of Ubuntu had issues with x300-x1900 ATI cards. Everyone experienced the same thing I did. Only it could be fixed by getting to a console and typing in a sudo line of some sort. Not sure how I can get to a command line if I can't even boot up. Maybe I'll just wait until the next release to give Ubuntu a shot.

Hey bud, don't give up.  Guess what card i'm using right now.  ATI x1300.  Although I must say, I did not experience any of the issues you are having.

I'm not any Linux expert or anything, so I can't really help you that much.  But I can tell you it is fully possible.  

I have been through the worst of the worst, getting wireless internet to work , java, ect.

---

