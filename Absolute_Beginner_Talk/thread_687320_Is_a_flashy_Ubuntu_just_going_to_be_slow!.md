---
title: "Is a flashy Ubuntu just going to be slow!?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Knacker on 2008-02-04
First off: thanks to everyone who has ever contributed advice in these forums: you guys are amazing!
For my question: Can someone tell me if I can expect a snappy desktop from a sexed-up Ubuntu?
I want the compiz-fusion stuff running, I want beagle, I also want one of those fancy docks (AWN, etc.). 
I'm using a Lenovo T61 (Core 2 Duo T7300, 3gb RAM, Nvidia 140m (128mb) video card, 5400rpm HDD...
My problem is that I've got all of this stuff running and everything is annoyingly laggy - especially firefox/swiftfox. Even when I turn all of this stuff off, what I'm left with is still not as snappy as XP (and it looks pretty dull).
Can someone tell me if I should be expecting all the..."bling" to run without any lag or if I will just have to deal with it...? 
I'm a bit heart-broken about this. I was SO psyched about switching from years of XP, but the fact that this tricked out installation of ubuntu is laggier than vista is so disappointing. The only thing I can think to do is to reinstall or try another distribution or switch back to windows (sad)...? (If there's an obvious total fix, great; but I don't want to spend days fiddling in terminal, if I'm not sure it's going to make any real difference in the end.)
If someone could let me know whether I should be expecting less or what, I'd be really grateful. Is Ubuntu just going to be slow if I sex it up? Thanks!

---

### Post by Zero Prime on 2008-02-04
What are your computer specs?  I'm running Compiz-Fuzion and AWN with no more lag than a fresh XP install.  Boot up is kind of slow, but It was slow with Gutsy prior to even running the extra apps.

---

### Post by xpod on 2008-02-04
I have all that stuff running on most of our older machines and they all run fine.
Single core machines ranging from 1.4 to 3.2Ghz  with between 512MB & 1G of Ram.

My new one here with it`s AMD 4000 cd x 2 2.1Ghz,2G of Ram and onboard Geforce 7 flys along.....in fact it`s so quick that it`s making me feel even older than i am:)

> What are your computer specs? I'm running Compiz-Fuzion and AWN with no more lag than a fresh XP install. Boot up is kind of slow, but It was slow with Gutsy prior to even running the extra app

This gives it away me thinks ;-)

> I'm using a Lenovo T61 (Core 2 Duo T7300, 3gb RAM, Nvidia 140m (128mb) video card, 5400rpm HDD...

---

### Post by Knacker on 2008-02-04
> **Zero Prime said:**
> What are your computer specs?  I'm running Compiz-Fuzion and AWN with no more lag than a fresh XP install.  Boot up is kind of slow, but It was slow with Gutsy prior to even running the extra apps.

What other specs do you want to know? I included the important information, I think (Lenovo T61 with Core 2 Duo T7300 (2GHz), 3gb RAM, Nvidia Quadro NVS 140m...). Is there something else you want to know? I'm trying to run gutsy...
Thanks! :)

---

### Post by euler_fan on 2008-02-04
There are ways to reduce the footprint while keeping the bling. Try turning off some services you don't use/need. See [this thread about programs run on startup.]("http://ubuntuforums.org/showthread.php?t=619226") I turned off several and it had a big impact on my RAM usage.

---

### Post by jan quark on 2008-02-04
just my opinion

your graphic card my be to slow to handle all that eye-candy stuff
your cpu and ram are a OK

besides
I was also lured be the bells and whistles but afterwards I realized where the true beauty of linux lies

 not giving away the secret you have to find it by your own...:)

---

### Post by Knacker on 2008-02-04
> **jan quark said:**
> just my opinion

your graphic card my be to slow to handle all that eye-candy stuff
your cpu and ram are a OK

besides
I was also lured be the bells and whistles but afterwards I realized where the true beauty of linux lies

 not giving away the secret you have to find it by your own...:)

Ok. Thanks for the thoughts and suggestions.

Yah: The graphic card was my worry too. How is it that Vista can manage all the eye-candy and remain, over-all, snappier? 

Any other general advice on speeding things up? (My CPU + Memory usage are never high [unlike Vista!], and yet everything lags. Weird, no?.)

Thanks again!

---

### Post by xpod on 2008-02-04
I/we have Compiz etc running on machines with only 64Mb Nvidia/ATI cards and the only "bling" lacking is the water effects,due to lack of pixel shading abilities on those old things but apart from that......all runs just fine.

---

### Post by aeiah on 2008-02-04
is the video card integrated? im assuming you've installed the nvidia drivers, but perhaps the video card is only using 32mb of your system ram instead of the full 128mb?

---

### Post by mike-laptop-dot-local on 2008-02-04
Dig into the Compiz Settings Manager and click the General Options. Click the Display Settings tab and put a checkmark beside "Sync to vBlank".

Doing this seems to remove a lot of Compiz's CPU usage.

---

### Post by billgoldberg on 2008-02-04
> **Knacker said:**
> First off: thanks to everyone who has ever contributed advice in these forums: you guys are amazing!
For my question: Can someone tell me if I can expect a snappy desktop from a sexed-up Ubuntu?
I want the compiz-fusion stuff running, I want beagle, I also want one of those fancy docks (AWN, etc.). 
I'm using a Lenovo T61 (Core 2 Duo T7300, 3gb RAM, Nvidia 140m (128mb) video card, 5400rpm HDD...
My problem is that I've got all of this stuff running and everything is annoyingly laggy - especially firefox/swiftfox. Even when I turn all of this stuff off, what I'm left with is still not as snappy as XP (and it looks pretty dull).
Can someone tell me if I should be expecting all the..."bling" to run without any lag or if I will just have to deal with it...? 
I'm a bit heart-broken about this. I was SO psyched about switching from years of XP, but the fact that this tricked out installation of ubuntu is laggier than vista is so disappointing. The only thing I can think to do is to reinstall or try another distribution or switch back to windows (sad)...? (If there's an obvious total fix, great; but I don't want to spend days fiddling in terminal, if I'm not sure it's going to make any real difference in the end.)
If someone could let me know whether I should be expecting less or what, I'd be really grateful. Is Ubuntu just going to be slow if I sex it up? Thanks!

I have alot of the compiz effects/awn/screenlets active and my system is fast and response.

I run it on a dual core 3ghz, 784mb ram and an onboard ati with 384mb memory/. There are some effects that can cause lagging like: the blur option and some others. If you just use the cube, expo, animations, widget layer, everything should be fine.

---

### Post by Knacker on 2008-02-04
> **aeiah said:**
> is the video card integrated? im assuming you've installed the nvidia drivers, but perhaps the video card is only using 32mb of your system ram instead of the full 128mb?

Thanks again for all your help, folks.

How do I check whether my video card is using the full 128mb? 

This is driving me crazy. I've been comparing the performance of my old computer (P4 2.4, 512mb...old dell) running XP and my new machine running Ubuntu, and the XP is often faster! It's mostly in the little things, like switching between tabs in firefox. And the switching tabs was faster in XP even when I turned off all of compiz's video effects! Should I check out another distribution maybe? Is it worth reinstalling (maybe I buggered something along the way).

The only place I could find to look for info on graphic card was "Nvidia X Server Settings" (which I can only run from terminal...can't find it anywhere in menus)...and there, weirdly, there is only one number for memory and it's 512mb (which makes no sense at all to me). 

I thought ubuntu was going to be, if a bit more work (which I'm okay with!), at least always noticeably faster.

---

### Post by FuturePilot on 2008-02-04
Firefox is just slower (in terms of responsiveness) on Linux no matter what distro. It's just a Firefox thing. 
You can check all Nvidia related stuff by running
```
nvidia-settings
```

---

