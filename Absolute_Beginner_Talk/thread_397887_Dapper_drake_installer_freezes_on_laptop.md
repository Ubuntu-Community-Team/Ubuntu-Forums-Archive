---
title: "Dapper drake installer freezes on laptop"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by sandberg on 2007-03-31
New to these forums.. I've been using Ubuntu on my stationary computer for about a month now and it works perfectly. I'm so in love with it, that now I want to install it on my laptop as well. 

So I tried running the live session from my Ubuntu 6.06 LTS CD, just like on my stationary. Everything loads up fine (but I do get some strange messages during the 'loading hardware drivers' phase which I don't understand), but ubuntu starts up and the desktop is shown.

Now, i click the install icon and the CD starts reading, and after about two minutes (!) the window for the installer shows up, blank. The CD-reader is still working hard, and after another ten minutes, there still is no progress; the install window is grey and blank as before. At this point, I'm forcing a shutdown of the laptop.

Any ideas what might be going on here? I've checksummed the CD and tested my memory with aid of the same CD and everything checks out fine. Do I have any alternatives that might help me install Ubuntu on my hp laptop?

Thanks

---

### Post by codypumper on 2007-03-31
How much RAM does your laptop have? What brand is the laptop?

---

### Post by sandberg on 2007-03-31
It is a HP Pavilion ze4400 (hm, just like that tv-show)
mobile AMD Athlon XP2400+
1.79 GHz, 192 MB RAM

The performance is better than my stationary I think. Is there a difference between AMD and Intel computers regarding Ubuntu installation programs?

---

### Post by sandberg on 2007-04-01
The messages I get during the "loading hardware drivers" phase is:

```
[17179678.360000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179678.360000] ali mixer 1 creating error.
[17179678.364000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179678.364000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
```

What does all this mean? Could this be what's causing the freeze-ups?

---

### Post by anniya0n on 2007-04-01
Are u getting a correct resolution before u give install

---

### Post by sandberg on 2007-04-01
Everything looks fine, it just works very sluggishly. I tried opening a few windows in the  live session, like the device manager, and it took several minutes for them to show. 

I also tried starting it in safe graphics mode, but that looks exactly the same and works just as bad. 

I guess it's all about some sort of bad match with hardware and drivers somewhere but I'm not smart enough to figure out what :(

---

