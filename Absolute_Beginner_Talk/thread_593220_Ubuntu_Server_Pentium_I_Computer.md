---
title: "Ubuntu Server: Pentium I Computer"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by madmagic on 2007-10-26
Well the title says it all, basily i have a pentium 1 computer that i wanted to convert to a server. i found a way to get it to boot up, but i get stuck at unpacking linux server
would this be a ram problem or a processor?

---

### Post by taurus on 2007-10-26
Which release are you trying to install on that P1?  How much RAM does it have anyway?

How fast did you burn the .iso image?  Some old machines are having problems with fast burning CD media.

---

### Post by madmagic on 2007-10-27
im trying to run 7.10 ubuntu server with i belive 52 mbs of ram (lol), i have a spare hard drive i just might convert to ram if this works, and i belive i ran the image as a 52X speed. I have ubuntu installed, just not exactly running. dont need the cd any more i mean, this happens when i boot up

---

### Post by taurus on 2007-10-27
I recommend you burn that .iso image again but this time, try to burn it at 4x instead of at 52x.

---

### Post by madmagic on 2007-10-27
so this might fix my unpacking issue when i boot? hmm ok i will try this tommorow, getting late -_-

---

### Post by kvonb on 2007-10-27
You need to install the 386 kernel, the standard generic one doesn't work on older machines.

Unfortunately it's not easy to do that, see my guide here:

[http://ubuntuforums.org/showthread.php?t=455884](http://ubuntuforums.org/showthread.php?t=455884)

Good luck :)

---

### Post by tgalati4 on 2007-10-27
Try DSL, it will work better with your hardware.

---

### Post by 13thMonkey on 2007-10-27
Make sure you're using the Alternate Install CD rather than the standard LiveCD. I've managed to install Dapper on a P1 (though it had more memory). You're probably better off installing an older version of Debian or Slackware (which I eventually did) though.

---

### Post by Threbus5 on 2007-10-27
Oh my,

Only very early Ubuntu releases installed with less than 190 Mb RAM. I tried several. I believe that although Kubuntu 6.01 or so will run with 125 Mb RAM, it needed 190 Mb for the install.

So, first, if possible add some RAM. Minimum 190 but 256 or more is better. That may be impossible with the machine that you have. The other alternative is a non-Ubuntu release. DSL (as an earlier post suggested) that translates as "Damn Small Linux" - not swearing, that is its name - could potentially work for you. Or consider Knoppix. Although I do not remember Knoppix exact operating requirements it seems that 52 Mb might be too little RAM for it.

Realistically, if ALL you want is something such as a file server, maybe DSL or Knoppix would execute externally. You need not install the Linux but could run it from a floppy or CD.

Good luck

---

### Post by masunda on 2007-10-27
is it really feasible,i tried to install  ubuntu 7.04 on pentium ii 400Mhz ,with 128MB RAM,4GB but i failed.what could have been my problem

---

### Post by Frak on 2007-10-27
Running Ubuntu on a PI would be near impossible due to its lack of a math coprocessor, which is used by just about everything now.

---

### Post by Threbus5 on 2007-10-27
To: MASUNDA -

Add RAM. Try 256 or more. If the older versions required at least 190 it makes sense to need more for the newer versions.

Take care

---

### Post by kvonb on 2007-10-27
> **Frak said:**
> Running Ubuntu on a PI would be near impossible due to its lack of a math coprocessor, which is used by just about everything now.

You must be getting mixed up with the 386sx chips which had no maths copro.

Pentium class chips all have them, maybe you're thinking of mmx extensions, which only Pentium MMX / Cyrix P6 /AMD K6 2 chips have.

I had the same issue with an AMD K6-2/500, it boots from the install CD, and installs perfectly, but when you reboot you get stuck at: "Uncompressing Linux...".

It's because they removed standard 386 support from the default kernel when they created the hybrid/SMP "generic" kernel which covers 686 and K7 support.

You have to install the 386 kernel and it will work.

Or use Ubuntu Breezy Badger (5.10) or even older Warty Warthog (4.something).

---

### Post by madmagic on 2007-10-27
Good morning,
Well i just woke up but lastnight i was looking at the kernal, it sounds like it should work, if it doesnt ill try with a diffrent version of Linux

---

### Post by madmagic on 2007-10-27
Wow thanks alot for the advice, install an older kernal worked!

next big project, seeing if i can get 1gig of ram from another hard drive to work :P

---

