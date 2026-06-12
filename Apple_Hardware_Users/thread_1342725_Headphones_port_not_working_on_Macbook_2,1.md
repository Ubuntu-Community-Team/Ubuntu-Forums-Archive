---
title: "Headphones port not working on Macbook 2,1"
date: 2009-12-01
forum: Apple Hardware Users
---

### Post by killa.fr0gg on 2009-12-01
Hi there!

I just installed Ubuntu on top of OS X, and so far I am quite pleased with the experience. I have had a lot of fun customizing my OS thoroughly, the way computing should be! However, for some reason, I cannot seem to make sound go through my headphones jack. Sound plays normally through the system speakers, but when headphones or sound cable is plugged in all sound goes out. In this state, levelers and other sound indicators will confirm that whatever application is still playing sound.

Thank you very much for your help. I love this community.

---

### Post by linuxopjemac on 2009-12-01
run
```
alsamixer
```

and unmute the headphone jack (with m)

---

### Post by killa.fr0gg on 2009-12-01
Thanks so much, that worked like a charm! I'm curious, though, what is it that sets that as the default behavior and why? 

it seems like such an obvious solution for a "kink," why hasn't it been corrected in the default package yet?

---

### Post by Tompalaz on 2009-12-01
I have a MacBook 5,1, I have the same problem. I'd tried this solution however, when I run alamixer, I can't find headphone. Or could it be HP?

Running karmic

---

### Post by linuxopjemac on 2009-12-01
Try it.

---

### Post by killa.fr0gg on 2009-12-01
> **Tompalaz said:**
> I have a MacBook 5,1, I have the same problem. I'd tried this solution however, when I run alamixer, I can't find headphone. Or could it be HP?


when you run alsamixer (not "alamixer") the channel for the headphone jack will not state "headphones" or something similar. Insetad, it will be labeled "Speaker." Find which of those is muted ("mm" displayed at bottom of slider, for me it was the channel furthest right) and unmute it by pressing "m" with that slider highlighted. That should work--worked for me!

---

### Post by Tompalaz on 2009-12-01
Oh my fault, a typo ment alsamixer. 

I'll try that. Thank you.

---

### Post by hollowtd on 2009-12-27
well, solved for most perhaps. I'm trying to get my mic jack to work on my ubuntu 9.10 macbook. The speakers work and the mic work but not the jack???

---

### Post by Kyre on 2010-02-20
This fix worked perfectly for me on a macbook 2,1 running 9.10

Thanks for the help! :KS

---

### Post by Odin Overland on 2010-03-17
> **killa.fr0gg said:**
> when you run alsamixer (not "alamixer") the channel for the headphone jack will not state "headphones" or something similar. Insetad, it will be labeled "Speaker." Find which of those is muted ("mm" displayed at bottom of slider, for me it was the channel furthest right) and unmute it by pressing "m" with that slider highlighted. That should work--worked for me!

Wow - that could really use a better indicator of whether or not it is muted... not to mention what it is muting.  Oh well... still better than I could create for now.  Anyway, I now have headphones working too - thanks all.

---

### Post by Mr. ThreEye on 2010-03-22
Also works in Lucid Lynx Beta1 on Macbook rev1 1.83. Thanks!

---

### Post by J^3 on 2011-07-01
Brilliant!  I went through a bunch of other processes, but this simple step fixed it in moments.  Thanks so much!

---

