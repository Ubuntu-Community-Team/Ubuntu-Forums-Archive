---
title: "XGL minimum requirements?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-06-25
I didn't find any info on this so here I am asking, what's the minimum requirements to run xgl properly? Would the cheapest system76.com laptop maby be good enough?

---

### Post by Stolie on 2006-06-25
Try checking at compiz.net to see if they have any minimums. I assume that's what you want Xgl for, yes?

---

### Post by Dr. Nick on 2006-06-25
Really all you need I believe is a 3d accelerated video card, Thier are ways to run it on a non accelerated card ive just not done it before and doubt it would be as smooth. Just look for a nvidia card prefefrably, I think ati is getting better also so one of them may do it for you. If all you can find is some weird integrated card, xgl may be a bit harder to get going.

---

### Post by Donshyoku on 2006-06-25
The two cheapest laptops on System76 will run it fine.  They have either a GeForce 6600 (your best option), a GMA900 (915GM) or GMA950 (its successor).  

I have a 915GM and have run XGL through the Korrorra Live-CD.  It works great, but if you are using Ubuntu, you are going to have to go through quite a few steps to get it up and running.  (Even so, that can be said for any video card you get... XGL and Ubuntu aren't tightly integrated last I tried).

The two higher-end models on System76 use ATi cards and they are notorious for bad Linux drivers.  I don't have much experience with this, but supposedly, they are getting better as many users are now using ATi cards without problems.

---

### Post by gardara on 2006-06-26
Thanks for all your replies... Doesn't xgl require a strong cpu and a lot of ram too? Or does it only need a video card?

---

### Post by muep on 2006-06-26
Somewhere I think it was said that xgl+compiz require 256 MB or RAM to run... though it might have been the Kororaa LiveCD. 

Anyway, I've run XGL and compiz on a computer with a 600 MHz Celeron, 128 MB RAM and a 64 MB Geforce FX 5200 graphics card. I worked surprisingly well, even usable, though the difference to a more recent computer with Radeon 9600 XT was noticeable.

I think the requirements aren't very high :)

---

### Post by gardara on 2006-06-26
that's kinda surprising... as windows vista with full effects does have pretty high requirements....

so we see once and again, linux pwns windows!

---

### Post by gardara on 2006-07-12
system76 has changed the pangolin from nvida 6600 to Intel GMA 950 224 MB Integrated Graphics.
How good does xgl run on the intel gma 950? is it worse er better than the nvida 6600? I want to buy a system76 laptop that runs xgl perfectly. Will a intel integrated do the job or will I have to buy a lot expensiver laptop with nvida 7600?

---

### Post by MarkSheely on 2006-07-12
You may want to consider using AIGLX+Compiz.  Most people seem to have more success with AIGLX when using intel chipsets.

--Mark

---

### Post by gardara on 2006-07-12
does aiglx have all the same features as xgl? Isn't it more buggy/crappier than xgl?

---

### Post by The Noble on 2006-07-12
I think it has many of the same features, and might become a more poular choice, that is when the ati and  nvidia drivers progress a little more. (AIGLX is part of Xorg 7.1)

---

### Post by gardara on 2006-07-12
ok, so you guys don't think I should spend extra money for a nvida card to use with xgl and just buy the intel integrated graphics... ?

---

### Post by MarkSheely on 2006-07-12
As far as I can tell, the features are nearly identical.  I use AIGLX/Compiz on a cheap ($550) dell laptop.  I have 512MB RAM, Intel Celeron M processor (a pretty crummy processor), and an Intel video card with the 915 chipset.  Not the worst components, mind you, but certainly not high performance by any means.  I have AIGLX/Compiz (Quinn, not vanilla) running flawlessly on my system, with all the effects that the xgl/compiz folks have.  

I guess what I'm trying to say is, it sounds like Compiz is more important to you than xgl, per se.  There are other options than xgl if you want to use Compiz.  And, there are cheaper laptops you can buy that you can use to get those effects than the ones at system76, if price is your primary concern.

However, if you heart is set on a system76 laptop (I've heard some good things about them), why not give them a call?  I'm sure they're a helpful bunch over there.

---Mark
[email]marksheely@gmail.com[/email]

---

### Post by gardara on 2006-07-12
thanks for yur reply. I posted at system76 forums and got the answare that they hadn't tried out intel card with xgl but had heard that it would work... you can see my post here: [http://system76.com/forums/viewtopic.php?t=127](http://system76.com/forums/viewtopic.php?t=127)
I actually don't know much about xgl/compiz but want to run it like I have seen in many nice videos/screenshots... I didn't find much info on the intel integrated card and xgl when I was searching today...

Sorry if I'm being annoying, before I'm going to spend any money I want to be 100% sure to be able to run those amazing xgl/compiz effects I have seen.
The reason why I'm going to choose system76 is because the laptops from them work 100% with ubuntu, are customizable and pretty cheap...

---

### Post by John.Michael.Kane on 2006-07-12
Gardara i have tested the kororaa-xgl/live cd on a biostar-tforce board with integrated gpu set to use 64mb of ram, and it worked fine. also you may want to look at this [[COLOR="Red"]Xgl-Hardware advisory[/COLOR]]("http://en.opensuse.org/Xgl#Hardware_Advisory")

---

### Post by MarkSheely on 2006-07-12
You're not being annoying.  Its only annoying when people buy hardware without looking into whether or not it will actually do what they want it to do, and then complain about it in the forums when there's a problem.

--Mark

---

