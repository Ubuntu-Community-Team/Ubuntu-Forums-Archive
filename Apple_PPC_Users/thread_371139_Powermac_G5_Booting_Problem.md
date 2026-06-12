---
title: "Powermac G5 Booting Problem"
date: 2007-02-26
forum: Apple PPC Users
---

### Post by enp522 on 2007-02-26
Hey everyone.

I've just tried to install Ubuntu 6.10 on my Powermac G5. Here are my specs:

Dual 1.8 GHz PowerPC G5
1.5 GB DDR SDRAM
ATI Radeon X800 XT 256 Mb

When I boot from the CD I am greeted by the prompt.
Typing live and hitting enter doesn't work, my monitor starts searching for a signal and never finds one.

So I tried doing what the booter recommended and typing live video=ofonly.

When I do this the Ubuntu loading screen comes up but it appears as though the colors are all messed up. After the loading bar fills up my screen goes black and just stays there.

I tried letting it sit for 10 minutes and still nothing happened. The monitor isn't searching for a signal, it's just black.

So I was wondering if this is a known issue and if anyone could point me in the direction of a workaround. I tried searching the forums but I wasn't able to find a solution.

Any help would be great,

Thanks a lot.

---

### Post by didg on 2007-02-26
100% untested but you can try the following:
at yaboot prompt
```
live-nosplash-powerpc64 break=casper-bottom
```

After a while you'll get a shell prompt: $
type
```
mount -n -o bind /dev /root/dev
exit
```

startup should resume and your screen detected.

---

