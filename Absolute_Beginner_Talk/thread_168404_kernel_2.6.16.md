---
title: "kernel 2.6.16?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by rorschach on 2006-04-30
hey - I have read a bit about, and am interested in trying the 2.6.16 kernel. I noticed that there is a thread on how to compile my own kernel, I don't think I'm quite ready for that, however.

Is there a way for me to get the 2.6.16 kernel without completely upgrading my distro to dapper?

Also - I'm running Ubuntu, but would like to run KDE. How can I get KDE without reinstalling my entire system.

Thanks!

---

### Post by bluevoodoo1 on 2006-04-30
[QUOTE=rorschach]Is there a way for me to get the 2.6.16 kernel without completely upgrading my distro to dapper?

Also - I'm running Ubuntu, but would like to run KDE. How can I get KDE without reinstalling my entire system.[/QUOTE]

1. Yes, but you'll have to compile it (from that thread you noted)... This one is a good one... [http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

2. ```
sudo apt-get install kubuntu-desktop
```

You will then have both ubuntu and kubuntu on your system. When you login you will have the choice of either.

---

### Post by rorschach on 2006-04-30
ok, so, looking at that how-to, I think I can follow that.
Will installing linux-tree get the sources for 2.6.16?

In Synaptic, the latest version is listed as 2.6.12.16.1.

---

### Post by bluevoodoo1 on 2006-04-30
[QUOTE=rorschach]ok, so, looking at that how-to, I think I can follow that.
Will installing linux-tree get the sources for 2.6.16?

In Synaptic, the latest version is listed as 2.6.12.16.1.[/QUOTE]

If everything is working correctly on your system, there really isn't a need to compile a kernel from source. Most people do it to get support for hardware that can't be detected. If you simply want a "newer" kernel, why not just upgrade to dapper? but... to answer your questions.

You'd have to start the guide where it says "NOTE: HOWTO compile from a vanilla kernel from kernel.org" and simple adjust the kernel versions. 

and you can get the source here... [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.11.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.11.tar.bz2)

---

### Post by rorschach on 2006-04-30
Yeah, everything is working fairly well on my laptop right now - though it seems no manner of voodoo will make dri work with opengl in linux on it - *shrug* I finally caved and dual-booted my system this morning.

*anyway* in my attempts to get dri to work, I tried different distros as well as just working on my system under ubuntu - Suse 10.1 uses 2.6.16, and I saw a dramatic performance increase using Suse over this version of ubuntu. Unfortunately, a lot of other things didn't work, and I am back on Ubuntu.

I have also tried running Dapper on my system, and it seems to break things (most significantly Xorg) so, I just want the kernel, because the performance increase I saw was simply too much to ignore.

---

### Post by bluevoodoo1 on 2006-04-30
Well I'm all for experimentation, but realize that the kernels provided with Ubuntu are tailored to Ubuntu rather than kernel.org's more generic variety. On breezy I had used a compiled 2.6.15 (with hopes it would fix a DMA problem) and there was a big leap in speed, especially booting and shutdown, but there were also other problems it created. I went back to the 2.6.12 until upgrading to Dapper (which is now the 2.6.15-21 kernel). So if you want to mess around around with it, I say... why not!?

---

### Post by rorschach on 2006-04-30
eh - why not - this build of ubuntu has been on my system for a good 4 hours... I'll try an upgrade to dapper. if it doesn't work, well, I'll just reload, I guess.

---

### Post by rorschach on 2006-04-30
Well, the deed is done... and Xorg is still running. Cool.
Now to go to 2.6.15-21-686... and to see if I can get multimedia to work.... that would be good
```
derrick@anubis:~$ uname -a
Linux anubis 2.6.15-21-386 #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006 i686 GNU/Linu x

```

Thanks for the nudge to dapper again - I guess some issues were resolved.

---

### Post by rorschach on 2006-04-30
Nifty - 686 version of the kernel installed... and working pretty well... maybe not as fast as 2.6.16, but it is hard to honestly compare.

Multimedia is coming along. learning my way around amaroK
I must say, kde is pretty slick. Makes me kind of sad (again) that I have to dual boot to run WC3 and WoW. *shrug*

Overall, though, I'm liking this. I've been pleasantly surprised with most of the apps I've been using.

Thanks again!

---

### Post by bluevoodoo1 on 2006-04-30
Alright!!

---

