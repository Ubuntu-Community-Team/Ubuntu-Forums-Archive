---
title: "amd 64"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by bibliolib on 2007-01-12
i downloaded and installed (after gettign a hardware modem) the latest ubuntu version.  asd i have been reading, i am seeing that sometimes there is a different cd needed for amd 64.  did i need to install a different version than the iso image i downloaded?  i couldn't find one for amd 64.  does that make sense?

---

### Post by maxamillion on 2007-01-12
not quite clear enough for me to give you an answer ... can you elaborate or maybe word it differently?

---

### Post by jvc26 on 2007-01-12
I think what is meant is as follows:
He's downloaded 6.10 (Edgy) and has a 32bit version at a guess. He's taken a look at the forums, read a 64bit edition exists and is wondering whether he has to install it.

If I am correct the answer is:
The 32bit version will work fine on amd64 but it won't be 64bit (unsurprisingly) If you want to run 64bit ubuntu you need to download the 64bit image (see the ubuntu downloads page) You dont have to install it if you dont want to, but for 64bit OS you have to.

Hope that helps,
Il

---

### Post by bibliolib on 2007-01-12
> **maxamillion said:**
> not quite clear enough for me to give you an answer ... can you elaborate or maybe word it differently?

sure  :-).  i have an amd 64 processor.  when i downloaded the iso image in order to install ubuntu 6.10, there were not  iso images for different processors listed so i downloaded just the regular 6.10 version.  after doing some reading, i have seen places where it is mentioned that if you ahve an amd 64 processor, you should use the ubuntu version for gthat processor.  do i need to do that?  or does version 6.10 automatically configure itself for whatever processor you have?

---

### Post by jvc26 on 2007-01-12
If you want 64bit support you have to download the 64bit image. If you dont mind running 32bit then you can just install the one you've already got. You can run either 32bit or 64bit on a 64bit processor, but only 32bit on a 32bit processor.
Il

---

### Post by bibliolib on 2007-01-12
what is the difference in 32 bit and 64 bit support?  i have no idea.  and, will having the version for my processor make things even faster?

---

### Post by jvc26 on 2007-01-12
The difference is, 32bit on a 64bit processor: It will only run in 32bit mode, (like you having a 32bit processor). 64bit version, on a 64bit processor can make full use of the 64bit processor's speed, hence should run faster. To be honest on the whole you wouldnt notice the difference I dont think. 
Il

---

### Post by G Morgan on 2007-01-12
No point in using 64 bit OSes until programs that need it exist. Note that getting Flash etc to run if you want it will be much more difficult under 64 bit than normal 32 bit.

Really AMD 64 is for bleeding edge types that don't mind things breaking or just not working at all. (note that I expect everything provided by Ubuntu will work but if you want other things you may run into trouble)

---

### Post by Hendrixski on 2007-01-12
As far as I know there's only one operating system that works on a 64 bit platform well.  And that is Solaris UNIX, it's been running on 64's for at least 5 years now.  It even comes with a really nifty java desktop service, and all of the applications you would expect.

I would like to know how far along Linux is coming with making more applications truly 64-bit compatible. I know when Windows tried it with XP-64, half of the OS was pulled out of it because it would crash woefully.

---

### Post by Hendrixski on 2007-01-12
> **bibliolib said:**
> what is the difference in 32 bit and 64 bit support?  i have no idea.  and, will having the version for my processor make things even faster?

The difference is how big of an address your processor could handle.  32 bit processing only handles an address size of 2^32, or 4,294,967,296 bits. about 4 megabytes.  a 64 bit processor can handle 1.8 x 10^19 ... so about 1.8 gig.

How does this help you may ask, if your memory is more than 4 megs, your addresses then point to a table, which then points to the memory address.  This is slow.  If you have the 64bit chip, no lookup tables, just lightning fast performance.

---

### Post by Ocxic on 2007-01-12
I'm using the 64bit ubuntu, and I've had now problems so far, I used automatix2 64bit edition to install the stuff i needed, even gave me 32bit swiftfox and flash with sound. the only real probleme i have is not being able t0o use .rar files as there in so 64 bit rar app. but there is a fix for this I'm just lazy.

I waould suggest that you install the 32bit library's in synaptic also, for compatibility sake, it helps. (just search for 32bit in synaptic.)

---

### Post by mikewhatever on 2007-01-12
Hi Bibliolib, check if your iso file is this: 'ubuntu-6.10-desktop-i386.iso'. If it is you are just fine and picked the best choice.

Read here about 64 bits : [http://en.wikipedia.org/wiki/64_bits](http://en.wikipedia.org/wiki/64_bits)

---

