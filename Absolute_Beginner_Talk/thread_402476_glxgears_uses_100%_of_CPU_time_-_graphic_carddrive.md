---
title: "glxgears uses 100% of CPU time - graphic card/driver problem?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by happycamper on 2007-04-05
System:  1.8 GHz Pentium III, ATI "All-In-Wonder" Radeon 9600 graphics card, 800 Mb RAM, dual-boot with Windoze XP, but Ubuntu has its own HDD with about 50 Gb free space (ext3 file structure).

I installed 6.06 ~3 weeks ago, following the instructions for the ATI graphics driver, and at first it ran great.  But gradually 3-D screensavers like Skyrocket, MatrixView and Flock began to run very slowly, so I began to suspect a problem with the graphics card interface.  I read in a forum here that the speed at which glxgears runs is a good measure of a card's 3-D acceleration capabilities, but when I ran that in a mid-sized window the gears turned normally for ~ 1 second and then slowed to a jerky crawl.  I tried it again with the system monitor on in the background and it showed 100% CPU use when the glxgears program was started (continuing until that program is stopped), so I suspect the CPU may be being called upon to do the work that the graphics co-processor  should be doing, but who knows?  Not me, for sure.

The same card works perfectly on heavily graphical games like Star Wars Battlefront III running under MS XP, so I doubt there is anything wrong with the card itself.  TIA for the help.

---

### Post by yabbadabbadont on 2007-04-05
One of these days, I'll get tired of answering this question...  :D

That is normal.  Glxgears renders as many frames as it possibly can as fast as it possibly can.  Hence the 100% CPU utilization.

---

### Post by happycamper on 2007-04-05
Thank you for your answer.  But is it normal for the gears to move extremely slowly, with a jerky motion, even in a mid-size window, and with nothing else running?  (I ran glxgears as a graphics test, not for fun).

---

### Post by wcattey on 2007-04-09
Perhaps I can be helpful here.  (But I also have a question about Ubuntu's implementation
of glxgears.)

The reason why the gears appear to move slowly is that they move the gears a bit for every frame update.  Just as you see the spokes of a wagon wheel appearing to move backwards when the
wheel passes you by, the motion you see is a complex artifact of the actual motion, and how
the display is perceived by the eye.

In my opinion, the real value of glxgears is that message you get of how many frames
per second it was able to push through the graphics device.

And that brings me to my question:

I'm running Ubuntu 6.10 on a Dell Optiplex 745 with an ATI Radeon x1300 Pro graphics card, with the default X server and drivers from the live CD install.

I've run glxgears to get a sense of how fast the GL refresh rate is, but I see NO messages from glxgears on how many FPS it managed.  It's been running for a couple hours, but NO reports.
Is the Ubuntu version of glxgears different, and not supposed to print out the refresh rate?  Or do I have a bug?

Thanks in advance,

-Bill Cattey
New to Ubuntu TODAY.

---

### Post by igknighted on 2007-04-09
> **wcattey said:**
> Perhaps I can be helpful here.  (But I also have a question about Ubuntu's implementation
of glxgears.)

The reason why the gears appear to move slowly is that they move the gears a bit for every frame update.  Just as you see the spokes of a wagon wheel appearing to move backwards when the
wheel passes you by, the motion you see is a complex artifact of the actual motion, and how
the display is perceived by the eye.

In my opinion, the real value of glxgears is that message you get of how many frames
per second it was able to push through the graphics device.

And that brings me to my question:

I'm running Ubuntu 6.10 on a Dell Optiplex 745 with an ATI Radeon x1300 Pro graphics card, with the default X server and drivers from the live CD install.

I've run glxgears to get a sense of how fast the GL refresh rate is, but I see NO messages from glxgears on how many FPS it managed.  It's been running for a couple hours, but NO reports.
Is the Ubuntu version of glxgears different, and not supposed to print out the refresh rate?  Or do I have a bug?

Thanks in advance,

-Bill Cattey
New to Ubuntu TODAY.

Try this instead (you need to tell glxgears that you want the fps printed):
```
glxgears -printfps
```

---

### Post by wcattey on 2007-04-09
Thank you!  Yes, that did it.

I am mystified why this some versions of glxgears have this option turned on by default,
and others do not, but that none of the versions obey the --help option.  The version of glxgears
in Ubuntu apparently was installed without a man page, and the other version I was using
had no mention of a "-printfps" option.

Oh well, at least I'm able to benchmark the default graphics.
Thanks again!

-Bill Cattey

---

### Post by RTrev on 2007-04-13
Just curious, but what kind of numbers are you folks seeing for -printfps on the glxgears?

I'm getting about 5250.something - is that "good"? 

Thanks,
Bob

---

### Post by TheRingmaster on 2007-04-13
Heres' mine. I don't have modern hardware though, but it not bad either. My gears run nice and smooth. No jitters what so ever. I have the nvidia-glx package installed. You can see my computer's specs in my sig.

---

### Post by wcattey on 2007-04-13
5250 is QUITE good!

I've been playing with Dell's most recent Optiplex line, the 745 paired with a high performance graphics card, the ATI Radeon X1300 Pro. (Not necessarily gaming quality, but apparently reasonably studly.)

I've been playing with a variety of for-pay Linux distributions on this hardware, as well as Ubuntu.

The vanilla un-accelerated X server from Red Hat and SuSE runs glxgears at ~900 fps.

When I  added the proprietary driver from the ATI web site, but screwed up the build of the kernel
module that does the hardware assist for 3-d rendering, glxgears slows down to ~300 fps.

Stock Ubuntu ran at ~300 fps as well. I think it was because it was building in powerful GL rendering functions that were not part of un-accelerated X servers.

When I added the full-blown build of the proprietary driver from the ATI web site including the kernel module, glxgears ran at ~4800 fps under Ubuntu, SuSE and Red Hat.  (Red Hat 4.  The ATI driver does not yet do Red Hat 5.)

Other systems with, for example the on-board Intel 845 or 945 chip sets seem to run at around 400 to 900 fps.

I was quite pleased with 4800 fps.  You should be QUITE pleased with 5250.

-Bill Cattey
MIT Linux Platform Coordinator.

---

### Post by RTrev on 2007-04-13
Thanks for the reply.  I'm experimenting with a new system, and not sure that I'm getting all I can out of it.  Here are typical values:

```

bob@bob-desktop:~$ glxgears -printfps
26527 frames in 5.0 seconds = 5305.323 FPS
26549 frames in 5.0 seconds = 5309.741 FPS
26548 frames in 5.0 seconds = 5309.414 FPS
26556 frames in 5.0 seconds = 5311.122 FPS
26554 frames in 5.0 seconds = 5310.605 FPS
26557 frames in 5.0 seconds = 5311.319 FPS
26551 frames in 5.0 seconds = 5310.024 FPS

```

The machine is a MachSpeed MSNV-939 NVIDIA motherboard with an AMD Athlon 64 X2 3800+ 2.0GHz, with 1.5G of DDR400, and a XFX GeForce 7300 GT / 512MB GDDR2 / PCI Express / Dual DVI video card.  I'm running Ubuntu 6.10, and am both fairly new to Linux and also to 64-bit.  I have no idea if the video is running about as fast as it should - hence my question.  The whole system seems really fast for normal work, but I'm not sure my DVDs look quite as good as they used to.  I'm looking into what I might do to fine-tune things a bit.  If these number look about in the ballpark for what this setup should be able to do, then perhaps there are some other tests or checks I should be running.  Appreciate the input.

---

### Post by igknighted on 2007-04-13
> **RTrev said:**
> Thanks for the reply.  I'm experimenting with a new system, and not sure that I'm getting all I can out of it.  Here are typical values:

```

bob@bob-desktop:~$ glxgears -printfps
26527 frames in 5.0 seconds = 5305.323 FPS
26549 frames in 5.0 seconds = 5309.741 FPS
26548 frames in 5.0 seconds = 5309.414 FPS
26556 frames in 5.0 seconds = 5311.122 FPS
26554 frames in 5.0 seconds = 5310.605 FPS
26557 frames in 5.0 seconds = 5311.319 FPS
26551 frames in 5.0 seconds = 5310.024 FPS

```

The machine is a MachSpeed MSNV-939 NVIDIA motherboard with an AMD Athlon 64 X2 3800+ 2.0GHz, with 1.5G of DDR400, and a XFX GeForce 7300 GT / 512MB GDDR2 / PCI Express / Dual DVI video card.  I'm running Ubuntu 6.10, and am both fairly new to Linux and also to 64-bit.  I have no idea if the video is running about as fast as it should - hence my question.  The whole system seems really fast for normal work, but I'm not sure my DVDs look quite as good as they used to.  I'm looking into what I might do to fine-tune things a bit.  If these number look about in the ballpark for what this setup should be able to do, then perhaps there are some other tests or checks I should be running.  Appreciate the input.

Note that this is not a benchmark.  Download a game like the UT2004 demo or Sauerbraten and check your FPS there for a real benchmark.

---

### Post by RTrev on 2007-04-13
> **wcattey said:**
> 
I was quite pleased with 4800 fps.  You should be QUITE pleased with 5250.

-Bill Cattey
MIT Linux Platform Coordinator.

Ah, good to hear!  I guess we posted simultaneously, but I put my hardware in the last post.  I really have no feel for the numbers, but this machine sure feels fast, and it's running at 26C as I work.  I went up to 33C when I had 5 instances of glxgears running.  I just put a new cpu fan on it, and wanted to make sure it was doing its job!  :)

I'm not sure my DVD movies look quite as good as they did on my previous and much slower machine, but that may be because I messed up VLC or something.  Have to do more research into video.

I mainly got this setup for actual work, with a couple of big LCD monitors so I could have lots of windows open and be able to see what I was doing.  Now that I have it running nice and stable, I'll get the other monitor out of the box and start messing around with Twinview.. which I hear can be hard to configure correctly.

Thanks for the feedback!

---

### Post by RTrev on 2007-04-13
> **igknighted said:**
> Note that this is not a benchmark.  Download a game like the UT2004 demo or Sauerbraten and check your FPS there for a real benchmark.

Okay, I'll go and look for them.  Would these also be a good indicator of how well the machine should simply play movies, or are we getting into hard-core gaming here?  I'm not really a gamer at all.. just looking to see if this system, which I got primarily because I wanted a fast machine with big monitors for doing web development work, was set up correctly and taking advantage of the hardware reasonably well.  I do enjoy my DVD music videos, though, and who knows.. I suppose I might get hooked on gaming someday.   :)

Thanks..

---

### Post by igknighted on 2007-04-13
> **RTrev said:**
> Okay, I'll go and look for them.  Would these also be a good indicator of how well the machine should simply play movies, or are we getting into hard-core gaming here?  I'm not really a gamer at all.. just looking to see if this system, which I got primarily because I wanted a fast machine with big monitors for doing web development work, was set up correctly and taking advantage of the hardware reasonably well.  I do enjoy my DVD music videos, though, and who knows.. I suppose I might get hooked on gaming someday.   :)

Thanks..

Yeah, if thats what you want you are set up fine. I do find it interesting, looking at your specs next to mine, how various components play a role in this.  Here are my specs and my glxgears output:

AMD Athlon64 X2 3600+ (65nm process, socket AM2) 1.9 Ghz
1gb Patriot RAM DDR2 PC2-5300 (667mhz)
Nvidia GeForce 6600GT 128mb GDDR3 RAM PCI-E
Fedora Core 6 32bit (though similar scores were seen in Edgy and Feisty 32bit as well)

```
[df4@localhost ~]$ glxgears
30516 frames in 5.0 seconds = 6103.182 FPS
30413 frames in 5.0 seconds = 6082.504 FPS
30476 frames in 5.0 seconds = 6095.139 FPS
30618 frames in 5.0 seconds = 6123.597 FPS
30476 frames in 5.0 seconds = 6095.129 FPS
30590 frames in 5.0 seconds = 6117.903 FPS
30499 frames in 5.0 seconds = 6099.632 FPS
30507 frames in 5.0 seconds = 6101.257 FPS
```

And I had almost 7,000 FPS before I played Sauerbraten for an hour... I guess it really is quality over quantity in a lot of respects in regards to components, wow... although I suppose it would take some real benchmarks off of games to see for sure.

---

### Post by RTrev on 2007-04-13
> **igknighted said:**
> Yeah, if thats what you want you are set up fine. I do find it interesting, looking at your specs next to mine, how various components play a role in this.  Here are my specs and my glxgears output:

AMD Athlon64 X2 3600+ (65nm process, socket AM2) 1.9 Ghz
1gb Patriot RAM DDR2 PC2-5300 (667mhz)
Nvidia GeForce 6600GT 128mb GDDR3 RAM PCI-E
Fedora Core 6 32bit (though similar scores were seen in Edgy and Feisty 32bit as well)

```
[df4@localhost ~]$ glxgears
30516 frames in 5.0 seconds = 6103.182 FPS
30413 frames in 5.0 seconds = 6082.504 FPS
30476 frames in 5.0 seconds = 6095.139 FPS
30618 frames in 5.0 seconds = 6123.597 FPS
30476 frames in 5.0 seconds = 6095.129 FPS
30590 frames in 5.0 seconds = 6117.903 FPS
30499 frames in 5.0 seconds = 6099.632 FPS
30507 frames in 5.0 seconds = 6101.257 FPS
```

And I had almost 7,000 FPS before I played Sauerbraten for an hour... I guess it really is quality over quantity in a lot of respects in regards to components, wow... although I suppose it would take some real benchmarks off of games to see for sure.

That *is* interesting!  Not knowing a lot about this, my guess is that you have faster memory?  Both on the system and in the video card?  Seems to be about the only thing different, doesn't it?  I'm running the 64-bit Ubuntu.. perhaps that factors in somehow?  I notice you're running 32-bit systems.

BTW, what does having played Sauerbraten for an hour have to do with your speed?  Did you over-heat and the system throttled you back a bit?  Are you over-clocked or anything like that?

---

### Post by wcattey on 2007-04-14
Depending on how the DVD player renders the image from the MPEG encoding,
the results you get from glxgears, or a game may or may not be indicative of how
much to expect from playing DVDs.

I hope someone who knows a lot about the sorts of work done by the DVD players can
chime in here with a clear description of similarities and differences.

---

### Post by igknighted on 2007-04-14
> **RTrev said:**
> That *is* interesting!  Not knowing a lot about this, my guess is that you have faster memory?  Both on the system and in the video card?  Seems to be about the only thing different, doesn't it?  I'm running the 64-bit Ubuntu.. perhaps that factors in somehow?  I notice you're running 32-bit systems.

BTW, what does having played Sauerbraten for an hour have to do with your speed?  Did you over-heat and the system throttled you back a bit?  Are you over-clocked or anything like that?

I'm not entirely sure, but that was the only thing I had done in the meantime :).  In windows I would expect a slowdown, as little things get left in memory in what not, but I've never seen it in linux before.

Yes, GDDR3 is faster and my system ram is also faster... but I bet in a really high end game you could outperform me because your 512mb of vram would be able to muscle though the far more intense graphics.  Oh, you know what... I heard that if a program is running 32 bit in a 64 bit environment (could glxgears be doing this?) there is a performance hit... so maybe this is the issue?

---

### Post by RTrev on 2007-04-14
> **igknighted said:**
> I'm not entirely sure, but that was the only thing I had done in the meantime :).  In windows I would expect a slowdown, as little things get left in memory in what not, but I've never seen it in linux before.

Yes, GDDR3 is faster and my system ram is also faster... but I bet in a really high end ame you could outperform me because your 512mb of vram would be able to muscle though the far more intense graphics.  Oh, you know what... I heard that if a program is running 32 bit in a 64 bit environment (could glxgears be doing this?) there is a performance hit... so maybe this is the issue?

Could be any or all of the above, I guess.  Interestingly, I installed Feisty (Ubuntu 7.04 which is due to be released any day now) and it has a "Restricted Drivers Manager" component, where you can download the latest driver that *they feel* is stable and safe to use.  That brought my numbers down quite a bit, as I had been using the latest one from the NVidia site before.

```

20237 frames in 5.0 seconds = 4047.282 FPS
19652 frames in 5.0 seconds = 3930.347 FPS
18526 frames in 5.0 seconds = 3705.077 FPS
18495 frames in 5.0 seconds = 3698.896 FPS
18496 frames in 5.0 seconds = 3699.082 FPS
18969 frames in 5.0 seconds = 3793.794 FPS

```

Or who knows, it could be Feisty itself.

In any event, I have a couple of bottlenecks on this system that I can't afford to fix yet.. a single 250G IDE hard drive, and the single channel memory.  I'll upgrade those whenever I can afford to, and can talk my wife into it.  :)  The video card was only about $75 or so, which made me wonder what the high-end cards had that this didn't.  I guess the faster memory is one thing.

It'll do great for my purposes, and if I get into gaming then I'll see what I need to change.

Appreciate your feedback here, everyone!

---

