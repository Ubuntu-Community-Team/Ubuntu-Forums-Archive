---
title: "Data verification app"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-04-18
Anyone know of a good app to use to verify the data on a dvd?

---

### Post by kidders on 2007-04-18
Hi there,

Perhaps **cdck** would do the job?

```
kidders@x2:~$ apt-cache search verify dvd
cdck - verifies the quality of written CDs/DVDs
```Assuming you didn't make the DVD yourself, I find myself wondering what you want to verify your data *against* though.

---

### Post by Stickymaddness on 2007-04-18
Thanks, I'll check that out, sounds perfect...

It's for a bunch of backup dvd's that I wrote and didn't verify at the time. I want to know my data is safe (as can be on optical media) before I delete everything off my drive...

---

### Post by kidders on 2007-04-18
Hmmm... I may be wrong, but the only way to know that would be by examination. Without comparing against an existing on-disk copy, you would have no way of identifying missing data, or data that was simply misread at the time it was burnt onto disc. (It seems to me that well-written crap is still crap!)

---

### Post by Stickymaddness on 2007-04-18
Hmm....you do have a point... 

Pretty much I've backed up to 30 dvd's, and I want to check that they're ok before I format my hdd... 

The challenge of course would be lazyness vs certainty that the dvds are ok....

---

### Post by kidders on 2007-04-18
Ugh... that thought doesn't make me feel terribly comfortable. I wonder what the chances are that, of 30 DVDs, just *one* of them will screw up at some point, either while being sourced off the original filesystem, burned onto disc, sitting around on your desk, etc....

Naturally, as a third party, I will strongly advocate caution ... even if it's *excessive* caution ... so in that light, I can't help wondering if there's an alternative approach to whatever you're doing. Then again, all those discs might be perfectly fine!

My advice would be to play it safe, to be honest. If you take a short cut (albeit justifiable on the balance of probability), and then lose something important, you'll have all the time in the world to ask yourself why you didn't do it right when you could have! It's happened to me in the past.

At least try **cdck** ... assuming it's even any good. If you get a friend to bring over his laptop for the afternoon, you'll be done in no time. :-)

---

### Post by Stickymaddness on 2007-04-18
Yeah, I'm pretty much expecting at least half a dozen of those dvd's to give me grief...

Well essential stuff I have on a 2nd hdd...the stuff on the dvd's I want off my hdd for extra space, but want to keep for a rainy day...

cdck here I come....

---

### Post by meborc on 2007-04-18
> cdck (CD/DVD check tools) is a simple console program to verify CD/DVD quality. The known fact is that even if all files on the disc are readable, some sectors having bad timing can easily turn into unreadable ones in the future.

To get an idea about a disc cdck reads it sector by sector, keeping all reading timings and then tells you its verdict. Optionally it can write the timing table into text file usable by gnuplot(1) program, so you can draw some graphs out of it. 

i think the program does not compare the dvd to existing file, but just checks if it is possible to read the dvd and that all the info on it is accessible.

i might be wrong of course... it would not be the first time :D

---

### Post by kidders on 2007-04-18
> **meborc said:**
> i think the program does not compare the dvd to existing file, but just checks if it is possible to read the dvd and that all the info on it is accessible.

i might be wrong of course... it would not be the first time :DNope... I suspect you're exactly right. (That's the reason for the discussion.)

---

### Post by Stickymaddness on 2007-04-18
Well as a final comment (for now) I've used cdck, and I'm happy (as one can be after writing 30 dvd's) chck is a very simple, easy to use terminal app and it's pretty fast, checks a whole dvd in a few minutes! 

I know it's no guaranty, but I'm happy if cdck reports it can read all my dvds! 

Maybe I'll post an update when I haul them out one "rainy day".

Thanks for the help! (I've still got to get used getting everything I need from synaptic / apt!)

---

