---
title: "another basic external drive question"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by kiko72 on 2008-03-17
Here's something I posted elsewhere, in another thread - and hoping to get some help here.

Thanks in advance for any assistance.

....
I boot into Ubuntu from a 3.5" external (yup, needs power) and everything works great. Actually, I'm shocked at how well everything has been going with my new OS over the past three weeks!

But here's my noob question on this topic: I just got a LaCie 120g external 2.5" so I can run off USB power alone. My XP can see it just fine, but how do I get Ubuntu to recognize it? I really do want to use it for both OSs, and since it's FAT32 - I should be able to, right?

I'm using 7.04, by the way.

My little USB pendrive pops right onto the desktop whenever I plug it in (much to my amazement!), but I'm really not sure what to do about an actual external HD.

Please excuse the noobness if this is really some kind of easy mount question or something. I guess I don't really know much about mount either - since I'm really crawling out from under the Windows rock for the fist time.
...

---

### Post by hhhhhx on 2008-03-18
you can try to force mount it, also check to see if gparted recognizes it.

---

### Post by kiko72 on 2008-03-18
> **xhhux said:**
> you can try to force mount it, also check to see if gparted recognizes it.

I don't have gparted - but it sounds like something I need. I'll install it and see if I can figure it out.

Force mount?

---

### Post by kiko72 on 2008-03-21
gparted does recognize the drive as /dev/sdc. But I'm not sure what to do from here. I wanted to  format the whole thing as FAT32 (which it should already be), but I am not given that option when I choose sdc1. There's a sdc1 and sdc5 listed gparted partition window - when I plug in my little USB pendrive, there's just one FAT16 partition. Could it be that something in sdc5 is preventing me from full access to the external drive?

Basically, I need something that both windows and ubuntu can see/read/write.

---

