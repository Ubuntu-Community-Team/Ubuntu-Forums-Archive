---
title: "questions about video"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by xflbret on 2007-05-23
I have been searching these forums, and am very confused about something. Can someone explain what the following things are, and what the differences between them are?

fglrx
aiglx
xgl

And when I say 'explain", I mean really dumb it down. Assume I'm a 3 year old child or something.

Here is my ultimate goal here...I have a Dell Latitude D600, which has the (sigh) ATI Mobility Radeon 9000 chip. What I would LOVE to be able to do is to be able to run Feisty, and also run Beryl, or barring that, Compiz, or barring that, at least have the freedom to set my resolution to something below 1400. I have been researching and experimenting, but i think not knowing what the above things are is one obstacle keeping me from my ultimate goal. 

I have asked for help before, but no one has had success. One guy claimed to, but wouldn't back up his claim with proof. Anyway, I'm saying I guess I'm on my own, but I would appreiate any and all help offered to me. 

Thanks in advance.

---

### Post by Ek0nomik on 2007-05-23
[http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)

[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

[http://en.wikipedia.org/wiki/Aiglx](http://en.wikipedia.org/wiki/Aiglx)

I could start to explain them in a bit more detail, but I myself don't know much about them, and anything I would tell you, is more than likely on all three of those Wiki pages.

Having an ATI Card won't be a problem, at least not all the time.  ;)

The best thing you can do (after reading those articles if you think that will make you more comfortable) is to hit up Google and the Ubuntu Forums and see what people have done and what you can do.

I have been searching around for you, and I found this:  [http://ubuntuforums.org/showpost.php?p=2637423&postcount=5](http://ubuntuforums.org/showpost.php?p=2637423&postcount=5)

Maybe it will give you a little insight to the situation.  Just play around.  ;)

---

### Post by xflbret on 2007-05-23
so let me see if i got this...xgl and aiglx are pretty much the same thing, and fglrx is the video driver. so i would get fglrx squared away first, and then see about getting aiglx working?

---

### Post by Gen2ly on 2007-05-23
Fglrx is a flag the xorg-x11 server needs t run with ATI video cards, XGL and AIGLX are compositing managers - one will be needed if one wants to run beryl.

---

### Post by Bachstelze on 2007-05-23
Nope, XGL and AIGLX are not the same thing. Though they basically serve the same purpose, they do it differently. AIGLX is just a "layer" on top of Xorg, which is the X server you're currently using, while XGL is a completely different X server.

---

### Post by xflbret on 2007-05-23
so if I want to make my video work right in 7.04, I use the xgl then?

---

### Post by Bachstelze on 2007-05-23
What do you mean by "make my video work right" ?

---

### Post by xflbret on 2007-05-23
achieving at least one of the goals that I spelled out in my initial post. I would love to run 7.04 with a resolution of 1280. I'm gettin too old to see 1400 resolution.

---

### Post by xflbret on 2007-05-23
So, don't talk to me like a 3 year old child...talk to me like a three year old child who has been beaten about the head and ears with a sledgehammer. I mean REALLY, REALLY dumb it down!!!

I am running dapper right now. If I were to install feisty clean, where do I start after that? Do I install fglrx first? Do I install xgl first? Where do I start? Please help!

---

### Post by Terl on 2007-05-23
> **xflbret said:**
> So, don't talk to me like a 3 year old child...talk to me like a three year old child who has been beaten about the head and ears with a sledgehammer. I mean REALLY, REALLY dumb it down!!!

I am running dapper right now. If I were to install feisty clean, where do I start after that? Do I install fglrx first? Do I install xgl first? Where do I start? Please help!

You would start by installing your video drivers first (fglrx).  After that you can configure your display settings to handle the resolutions you need.  After you are happy with that you can move on to the other bits-XGL and AIGLX.  After all you need the video drivers before you can try the eye candy.

---

### Post by xflbret on 2007-05-23
agreed. when (if) I get to the point where the video drivers work well, do I install xgl, aiglx, or both? If both, which order?

---

### Post by xflbret on 2007-05-23
OK, so, I installed Feisty clean. I ran my updates, now I'm scared...I have done this many times before, now I'm at the part when I try to install video drivers, and then I can't start the xserver again. Well, I install ATI's 8.28.8 drivers, and it just wont let me, saying a bad substitution error. Then I try something else, and I can't start the xserver.

So, I really want to install some sort of better video drivers, and I want the xserver to start after I install them. how do I make this happen? Which drivers do I install?

---

### Post by Bachstelze on 2007-05-23
Feisty has Xorg 7.2 and the ATi drivers are not compatible with it. Downgrade to Edgy or don't use them and get a nvidia.

---

### Post by xflbret on 2007-05-23
will the open source drivers not work? Having to upgrade hardware to use an OS is kinda m$-vi$ta-like and not really the linux way, is it?

---

### Post by Ek0nomik on 2007-05-24
If you want to run Beryl you can setup a separate session that will run XGL.  That's how I got Beryl working a few months ago.  I don't use Beryl anymore though.

---

### Post by xflbret on 2007-05-24
> **Ek0nomik said:**
> If you want to run Beryl you can setup a separate session that will run XGL.  That's how I got Beryl working a few months ago.  I don't use Beryl anymore though.

how do I do that? I can never get that far

---

