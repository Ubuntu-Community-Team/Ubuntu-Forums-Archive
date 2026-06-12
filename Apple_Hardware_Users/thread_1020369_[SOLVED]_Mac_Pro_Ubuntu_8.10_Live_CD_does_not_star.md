---
title: "[SOLVED] Mac Pro: Ubuntu 8.10 Live CD does not start"
date: 2008-12-24
forum: Apple Hardware Users
---

### Post by Gsundbrunn on 2008-12-24
Hi,

merry christmas to all!

I´m a very proud owner of a MacPro (3.1) Intel with 2 x Quad-Core Intel Xeon 2.8 and 14GB Ram. A great machine - what I´m missing is my favorite OS - Ubuntu. I downloaded both live CD´s: 8.10 32 and 64 bit and tried to start both (just to see whether Ubuntu would work on my machine). 

Unfortunately both doesn´t start - nothing happens. No black screen, nothing. I always stick to the gray screen of the booting machine. Even, if I choose with "alt" during the boot the bootdevice and select the CD, nothing happens afterwards, except that my machine freezes.

I tried the CD at a MacBook Pro - and it worked. So the CD is fine.

Any hint or help appreciated. I would really love to get Ubuntu running on this very fast machine...

Regards

Stefan

---

### Post by skern03 on 2008-12-24
Nice machine! Are you bragging or asking for help :P???

Anyway, I don't have your particular problem since I'm not running this on a Mac, but I've never been able to get U8.10 to work. Tried it four times on two different drives, no luck. And we're not alone. See this poll; last I checked, a staggering number of people could neither upgrade nor install:

[http://ubuntuforums.org/showthread.p...+problems+ibex](http://ubuntuforums.org/showthread.p...+problems+ibex)

I would try two things: 1) Ubuntu 8.04 (which installs and runs perfectly on this machine); 2) burning the 8.10 CD at a slower rate to see if that fixes it.

If you can't get either to work, and you can get it to work on the other machine (which clearly demonstrates that the CDs aren't defective), then I'd visit a Mac support center and go see a Mac genius (hope I got that right). It's possible that your CD drive is defective.


> **Gsundbrunn said:**
> Hi,

merry christmas to all!

I´m a very proud owner of a MacPro (3.1) Intel with 2 x Quad-Core Intel Xeon 2.8 and 14GB Ram. A great machine - what I´m missing is my favorite OS - Ubuntu. I downloaded both live CD´s: 8.10 32 and 64 bit and tried to start both (just to see whether Ubuntu would work on my machine). 

Unfortunately both doesn´t start - nothing happens. No black screen, nothing. I always stick to the gray screen of the booting machine. Even, if I choose with "alt" during the boot the bootdevice and select the CD, nothing happens afterwards, except that my machine freezes.

I tried the CD at a MacBook Pro - and it worked. So the CD is fine.

Any hint or help appreciated. I would really love to get Ubuntu running on this very fast machine...

Regards

Stefan

---

### Post by Gsundbrunn on 2008-12-24
> **skern03 said:**
> Nice machine! Are you bragging or asking for help :P???

You´re kidding ;-)

Many thanks for your quick reply. I´m using this machine for a few month now and the CD Drive works perfectly. I would put that on the list of possible issues down to level 12. 

I tried OpenSuse 11.1, too - just to find out wheather this works or not. Unfortunately(?) not. So I will give the 8.04  try and will come back with the result later...

Regards!

Stefan

---

### Post by Gsundbrunn on 2008-12-24
Bad luck... I tried the 8.04. Same situation. It does not switch to the black screen, the Ubuntu menue.

I burned a CD with speed: 4 to eliminate any possible failure. Even this didn´t succeed.

Any help appreciated :-)

Regards

Stefan

---

### Post by Gsundbrunn on 2008-12-24
Next Update:

I instlled a different DVD Drive - same issue. Looks like the 2 x QuadCore isn´t supported :-(

---

### Post by cyberdork33 on 2008-12-24
> **Gsundbrunn said:**
> Next Update:

I instlled a different DVD Drive - same issue. Looks like the 2 x QuadCore isn´t supported :-(
several people have got Ubuntu installed on their Mac Pro, so I wouldn't say that.

---

### Post by skern03 on 2008-12-24
Hmm... i still think the Ubunutu installation CD would at least launch, yet you don't even get the first screen with the language selections...

I am SURE you already checked this... and let me first say, I'm not a Mac user, so I could be very wrong... 

In the BIOS, you can set the boot priority. Check it, and make sure the CD is set to boot first, then the hard disk, then whatever else (or nothing).

Does that help any?

> **Gsundbrunn said:**
> Next Update:

I instlled a different DVD Drive - same issue. Looks like the 2 x QuadCore isn´t supported :-(

---

### Post by cyberdork33 on 2008-12-24
> **skern03 said:**
> I am SURE you already checked this... and let me first say, I'm not a Mac user, so I could be very wrong... 

In the BIOS, you can set the boot priority. Check it, and make sure the CD is set to boot first, then the hard disk, then whatever else (or nothing).

Does that help any?
Macs do not have a BIOS, they have EFI, and there is not configuration utility for it.

There is a similar problem with certain iMacs and the latest release of Ubuntu. It might be the particular graphics card you are using or the monitor you have attached.

---

### Post by Gsundbrunn on 2008-12-24
I really tried everything...

Reduced the memory to 2GB. Tried 8.04 64bit, 8.10 32 + 64bit, SuSe 11.1 64bit, SuSe network installation disk...

Nothing...

Definitively very, very suspicious...

Regards

Stefan

---

### Post by skern03 on 2008-12-24
Although I'm not a big fan, you could try Kubuntu. K8.10 has a nice ui, but like it's sister, U8.10, seems a bit buggy. K8.04 is pretty stable. Still, since you said you already tried another OS (SuSe), it probably won't help matters.

I wonder if you can get assistance for this at an Apple store. Not likely, but maybe worth a shot...

> **Gsundbrunn said:**
> I really tried everything...

Reduced the memory to 2GB. Tried 8.04 64bit, 8.10 32 + 64bit, SuSe 11.1 64bit, SuSe network installation disk...

Nothing...

Definitively very, very suspicious...

Regards

Stefan

---

### Post by Gsundbrunn on 2008-12-25
I tried different Distros as well. What exactly happens is that in the moment the Ubuntu CD starts, the monitor does not get a signal. Ich checked that out. That - in my eyes - means, my graphic card isn't supported!

Would be interesting to know, which version of MacPro are running with Ubuntu and, which graphic card was built in.

Regards

Stefan

---

### Post by pxwpxw on 2008-12-25
> **Gsundbrunn said:**
> I tried different Distros as well. What exactly happens is that in the moment the Ubuntu CD starts, the monitor does not get a signal. Ich checked that out. That - in my eyes - means, my graphic card isn't supported!

Would be interesting to know, which version of MacPro are running with Ubuntu and, which graphic card was built in.

Regards

Stefan

Have you tried an Alternate install CD, the graphics are simpler and may be enough to get to the first screen with some video options.

---

### Post by Gsundbrunn on 2008-12-25
Let say it this way: the first - lets call it "ping" from the starting CD to the screen doesn not work. Independent of the version and the distro and so on.

I tested another CD and DVD with other content than Linux - and the starting of the content worked.

Its definitively related to the Linux CD´s...

Strange....

---

### Post by Gsundbrunn on 2008-12-26
To bring the topic up again - it´s really important for me as I´m donig my business partially with Linux.

The same CD´s are booting well on a MacBook Pro.

Regards

Stefan

---

### Post by Gsundbrunn on 2008-12-28
Hi,

issue is solved - I did a SMC reset and everything works well now. Inbetween a 8.10 64 bit is running very, very speedy on my machine ;-)

Thanks for all the tips inside here!

regards

Stefan

---

### Post by cyberdork33 on 2008-12-28
If you have anything to contribute, it would be very appreciated...
[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

---

### Post by skern03 on 2008-12-29
> **Gsundbrunn said:**
> Hi,

issue is solved - I did a SMC reset and everything works well now. Inbetween a 8.10 64 bit is running very, very speedy on my machine ;-)

Thanks for all the tips inside here!

regards

Stefan

Since this is solved, go up to the top of this thread, and click Thread Tools and mark it solved.

---

### Post by Gsundbrunn on 2009-01-01
Done!

---

