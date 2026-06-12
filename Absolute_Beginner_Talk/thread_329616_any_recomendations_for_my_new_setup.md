---
title: "any recomendations for my new setup?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by HighD on 2007-01-01
Ok so here's the deal...

I just bought a new PC, it's a Dell Dimension E520

-- Core 2 Duo E6300
-- 1GB DDR2 533MHz Ram, 
-- nVidia GeForce 7300LE 256Mb GPU(DVI)
-- Dell 19" 1907FP Digital Monitor(DVI)

So much faster than my previous Athlon XP 2400+...now I have some questions?

- which kernel to use?
- nVidia beta drivers or normal ones? ( I managed to use 1280x1024(native resolution), but I'm using the nv drivers)

also..

- has there been any issues concerning any of these components? (I know it's a lot to ask but just in case anyone knows!;) )

- is it wise to install ext3 support on Windows? (I'm dual-booting)
- I once read someone fried their DVI port by using ubuntu (mine works so far, with DVI), can that happen?

Any other recomendations to a newbie for this kinda setup? 

Well..thanks in advance for all your help, i really appreciate your answers. :mrgreen:

---

### Post by maniacmusician on 2007-01-03
I'm a bit interested in this as well. I'm going to go dual-core too (though I'll probably settle for a Pentium D) and i'm wondering what I'll have to do different to maximize the amount of processing power I can get out of a dual-core. Different kernel? interesting stuff.


As for the drivers, I always go with the beta ones just to be edgy. I like new stuff. I'm envious of your setup! my plan was to grab a new mobo, use a Pentium D 825 (i think thats the right number) and about 2 GBs of RAM. good luck with this, and I think i'll keep an eye on the thread also

---

### Post by pseudonym on 2007-01-03
> **HighD said:**
> Any other recomendations to a newbie for this kinda setup? 
You should check out [this]("https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28core%29%7C%28duo%29") wiki if you haven't already.

If you don't mind a slight increase in your learning curve you could also consider running 64-bit Ubuntu. Processor-intensive 64-bit apps eg. video editing experience a significant increase in performance. There aren't many apps these days which aren't compiled for 64-bit, but unfortunately some of those are very important ones like browser plugins and w32codecs. See the [64-bit forum]("http://www.ubuntuforums.org/forumdisplay.php?f=134") for more info and how to run these apps on 64-bit. It's not hard to set up.

If you don't want to go 64-bit yet, the i686-smp kernel on 32-bit ubuntu is what you want. That way you you get something which utilises your dual-core CPU.

As far as video card drivers are concerned, if you do anything multimedia or game related, your gonna want the nvidia drivers. You get 3D acceleration and everything looks so much better.

Personally, I wouldn't bother setting up windows for ext3 support, but that's probably because I don't use ext3 (except for my /boot partition) and I only [use windows]("http://www.ubuntuforums.org/showpost.php?p=1929486&postcount=22") for non-linux games. All your music and videos and what not can be played in linux so I don't see the need to have them accessible to 'another OS'.

Fried DVI? Can't see how that could in any way be caused by the OS. Must have been a hardware thing.

Good luck with it all anyway! :)

---

### Post by HighD on 2007-01-04
GREAT STUFF! Thanks pseudonym! 

I may use 64-bit Ubuntu....i don't mind the learning curve...

I will take a look to that wiki you sent...very interesting...I'm using a G965 Express motherboard...I'll let you know how everything goes...

Thanks guys

---

### Post by Crakie on 2007-01-04
About the video drivers: if you're into 'pimping' your system with things such as Beryl, I'd recommend giving the beta drivers of Nvidia a try. I rarely see people having problems with them anyway. They work fine for me too on C2D +7600GT.

---

### Post by maniacmusician on 2007-01-04
> **HighD said:**
> GREAT STUFF! Thanks pseudonym! 

I may use 64-bit Ubuntu....i don't mind the learning curve...

I will take a look to that wiki you sent...very interesting...I'm using a G965 Express motherboard...I'll let you know how everything goes...

Thanks guys
please do! I'm looking at the same processor as you, let me know if you're able to optimize it perfectly

---

