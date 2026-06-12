---
title: "GDM looping and now it's freezing"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-09-13
Hi,
I'm on Feisty, with an HP m7580n Media Pavilion. My GDM comes up fine during the boot, and at first this Feisty install was set and working fine. 

But now after I sign in at my GDM, my desktop starts to load but then it loops back to the GDM and I have to sign in again. At times, it is taking me 4 loops before it lets me on to my desktop for good.

And now I'm at my desktop and it's frozen.

After some searching, I ran this:

```
sudo aptitude clean
```

But that only seemed to make things worse. I appreciate any assistance anyone could offer. 

(An aside: There are times whether I wonder if Ubuntu is really as stable an OS as people are saying. Problems seem to crop up one after another at times. I've been using Ubuntu for 6 months now, and I do like it despite the problems)

I appreciate any help on this - Many Thanks, Frank B.

---

### Post by asmoore82 on 2007-09-13
What Video Card do you have/Does it use Shared Memory with RAM?
Have you tested the RAM?

and Bonus Question, have you used Automatix on this system?

---

### Post by Brightbelt on 2007-09-13
No, not at all. I learned my lesson with Automatix a while back!!

I have used EasyUbuntu with this install, and from what I've read, it generally gets more approval as a program from the Linux Gurus, though I could have missed something there.

I'm open to any ideas,....Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-09-13
I didn't see your other questions at first: 

I have an Nvidia 7600 GS which has been pretty flawless and I bought it while looking online with my iPhone at a list of supported video cards on the Ubuntu Documentation site.

As for whether it shares any RAM, that I do not know.

Thanks, Frank B.

---

### Post by Brightbelt on 2007-09-13
Ok, I just removed a GDM theme I had downloaded and am using a default GDM, and so far it's working better.

I'm going to reboot again to make sure there's any real difference.... ;) Frank B.

---

