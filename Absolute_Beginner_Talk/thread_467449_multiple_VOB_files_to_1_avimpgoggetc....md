---
title: "multiple VOB files to 1 avi/mpg/ogg/etc..."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-07
I'm looking for a good program that can take the 6 or 7 VOB files I have and pack them into ONE avi, or ogg, or mpeg, or anything else!  The features I'm looking for are:
1. for the sound and video to not go out of sync
2. possibly add black borders at top and bottom to change 2.1:1 into 4:3
3. don't care if it needs wine, just has to work!!!

This is has been a big annyoence for me and I've found no better process so far than this (I do this because of various problems in everything):

step 1: rip DVD in dvd::rip
step 2: make an DVD iso out of the VOB files using DeVeDe (adding black bars and compiling into one file (like I wanted!))
step 3: rip DVD iso with thoggen into single ogg

this works ok, but the quality by this point is not as good as the start of course, the lips are out of sync (big problem!) and the sound is kind of quiet.

Does anyone have a suggestion of a program that does what I asked for above in all one package? KDE, GNOME, need wine, all ok!

---

### Post by crispy_420 on 2007-06-08
Why not use thoggen directly?

---

### Post by finite9 on 2007-06-08
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs?highlight=%28rip%29%7C%28dvd%29#head-ac4cacf4f7cabb88847c3010fe3e1473b355bd89](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs?highlight=%28rip%29%7C%28dvd%29#head-ac4cacf4f7cabb88847c3010fe3e1473b355bd89)

This wiki details how to use Ripit4me under wine to rip any DVD into an ISO and you can choose if it will fit on one DVD or rip without loss.

K9copy in the repository does the same thing if you have feisty, but it's slower than Ripit4me to read the DVD.

Then you can use mencoder later to create XviDs or H.264 AVC versions that are much smaller.

Thoggen is in my opinion not an option, as I don't know many commercial players that support that format.  If it becomes more mainstream in the future like vorbis then it may become an option, but at the moment, we are sort of stuck with XviDs and H.264 due to market popularity.  besides this, it cannot rip later DVDs like K9copy or Ripit4me due to newer copy protection methods like blank titles.  K9copy has just recently fixed this in the feisty version but even rippers under windows have problems with newer discs, hence ripit4me.

---

### Post by ryanVickers on 2007-06-08
> Why not use thoggen directly?
Well, that's a good question, but here was the problem:
minor ones (didn't really turn me off too much):
-no ability to add black bars
-reduced quality to 63% at best settings

Major one (this was why I didn't use it):
-it ripped the chapters in the wrong order!

reply to second post coming soon! :)

---

### Post by ryanVickers on 2007-06-08
Ok, I think I like the k9copy, thanks!  I'll look around and see if there's anything that could be a problem - but so far, I think it's going to do everything just fine!

---

