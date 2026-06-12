---
title: "32 vs 64 bit"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-04-09
what's the advantages of 32 vs 64 bit operating systems and hardware?

---

### Post by SunnyRabbiera on 2008-04-09
well 64 bit is obviously more powerful, it has the extra kick that 32 bit lacks.
But there is a drawback, most software and even hardware is made for 32 bit systems.
Getting multimedia can be a rough ride, things like flash and certain codecs have been mainly targeted at 32 bit systems.
But 64 is gaining some ground, with dual core technology out there 64 bit could catch up sooner or later.

---

### Post by KCormier on 2008-04-09
From what I've heard, 32 bit support is usually a bit better (software & drivers) however 64 bit runs faster!

-Kevin

---

### Post by NightwishFan on 2008-04-09
Ok. I will start with my advice. Try out both. I prefer 64-bit as it is making full use of my hardware.

64-bit main disadvantage was lack of software compatibility but today that is not true. Programs will be more responsive and programs that rely heavily on processor power will see great improvement. (Games, audio/video converters/editors) By default it supports an absurd (from todays standards) amount of ram.

Disadvantages are sometimes you can have issues with obscure programs/drivers. Although I never had such issues myself.
[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by grazed on 2008-04-10
I think the issues  are more involved with windows over linux distros, no?

---

### Post by joshrobinson on 2008-04-10
64bit has almost no disadvantages as compared to 32bit
all the programs i use, are available in the repos now, which it wasnt before
all my drivers work fine, and all my multimedia is 100% working
all without hassle

64bit has come a long way compared to what it was on dapper

---

### Post by Perfect Storm on 2008-04-10
> **grazed said:**
> I think the issues  are more involved with windows over linux distros, no?

Yes.

I'm running 8.04 64-bit. I got flash, multimedia etc. without any problems.
If it's Open Source app/lib there's no problem to get 64-bit version of it and closed source stuff that only running 32-bit are now very easy to get running on 64-bit with "getlibs".

So it's a myth that 64-bit is harder and have less stuff.

*AI who switch from 32-bit to 64-bit a 1/2 year ago*

---

### Post by BaffledMollusc on 2008-04-10
Agree with josh robinson above.

64 bit is nothing magical, and will not guarantee you a speed increase. Unless you're running certain specialised applications, you'll only see a few percent speed up, and in some cases a slow down. If you're a typical home user and not running a server, there is effectively no performance difference.

It used to be that the 64-bit software ecosystem was not as mature as the 32-bit ecosystem, which used to make me recommend 32-bit over 64-bit for home users. Nowadays, however, 64-bit software support is getting  close to parity (apart from a few things like Flash, I think), so go for whichever one you want.

---

### Post by kpkeerthi on 2008-04-10
What about 64-bit flash and 64-bit java plugin? Are they available?

---

### Post by Saint Angeles on 2008-04-10
i'll run 32 bit until 64 bit is perfected.

my P4 has "hyperthreading" when running 32 bit which tricks the OS into thinking theres 2 CPUs.

its a good thing.

---

### Post by misfitpierce on 2008-04-10
The part about most software being for 32 bit is not really true anymore. Since 7.04 more and more programs have gone 64 bit as well. In fact I would say 98% of all programs are 64 bit as well and the ones that are not you can just run the 32 bit on 64 bit Ubuntu. 64 Bit has speed increases in moving files as well as running 64 bit app's which can be quicker as well. Try it out and you wont be disappointed... I wasn't :)

---

### Post by jhnphm on 2008-04-10
Running 64 Hardy here- I do indeed have problems w/ java plugin, and nspluginwrapper crashes like no tomorrow, so I'm just running the 32 bit stuff in a chroot.

Frankly, there's neglible benefit unless you're number crunching (media encoding, etc)  or you have >= 4GB of RAM like I do. In fact, w/ larger pointer sizes you might actually experience a slowdown


[http://www.phoronix.com/scan.php?page=article&item=616&num=3](http://www.phoronix.com/scan.php?page=article&item=616&num=3)

I attribute the posts supporting otherwise to be either the result of the placebo affect or just hype. :roll:

---

### Post by insane_alien on 2008-04-10
64-bit is a good thing, using ubuntu there is absolutely no problems getting software as the repositories are identical. everything works fine and 64-bit reallly speeds up some stuff i do which involves processing large datasets.

---

### Post by CJ56 on 2008-04-10
Curiously enough I've just switched from Gutsy 32 to 64 bit. I'm a really low-level user, no power applications, and on the plus side

- Stuff does work a little bit more snappily, always a good thing
- No apparent snags with Flash/codecs etc
- Nice warm glow from the feeling that I'm using the full potential of the PC

On the other hand, I couldn't get Opera to install, even with getlibs. Since I don't actually like Opera, no harm done, but that's one example of an application that I couldn't get to play

It's a close call, in other words. If you've got a fairly tried & true set of computing needs, it might be worth a go...

---

### Post by sayakb on 2008-04-10
There are absolutely no problems with 64-bit. All packages are available under the amd64 architecture. I have flash and all gstreamer codecs, everything. And those i386 packages with no 64-bit alternatives can be installed with --force-architecture option anyways. :)

---

### Post by kpkeerthi on 2008-04-10
What about java plugin in 64 bit?

---

### Post by Cadmus on 2008-04-10
I notice the main 64-bit concerns revolve around desktop apps, if one has a 64 bit server (later Xeon or the like) is there any reason not to go with the 64-bit Ubuntu?

---

### Post by sayakb on 2008-04-10
> **kpkeerthi said:**
> What about java plugin in 64 bit?

Why don't you search packages.ubuntu.com. You might get exactly what you need.

---

