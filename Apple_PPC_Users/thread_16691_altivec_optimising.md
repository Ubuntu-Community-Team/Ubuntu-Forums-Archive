---
title: "altivec optimising"
date: 2005-02-23
forum: Apple PPC Users
---

### Post by ssam on 2005-02-23
i just spotted this [http://www.ppczone.org/forums/viewtopic.php?t=142](http://www.ppczone.org/forums/viewtopic.php?t=142)

looks like a way of vectorising code to vastly speed up stuff on G4 and G5s

"I can definitely say from my benchmarks so far that the minimum
speed increase will be from 400% (in cases where vectorization is
difficult) to 3200%!! The average is about 1000% (10x). This will be
directly visible to the user in applications that require a lot of
processing power"

if this is true that is pretty cool. does anyone understand it enough to say how likely this is, and if heavey programs like the gimp and xine could be speeded up in ubunut?

sam

---

### Post by toojays on 2005-02-24
Yes, it is possible, but don't hold your breath. This kind of thing is not going to get mainstream until some time after gcc 4.0 is released.

Yes, gimp and xine are applications where this stuff will apply. I imagine that some parts of xine are already using Altivec; I know that mplayer uses it already. The difference here is that gcc 4.0 can automatically generate Altivec for certain kinds of code. Up until now people in the GNU/Linux world have had to do it by hand, which takes a lot of time.

Where he talks about a minimum of 400% increase, that is in the case where you can vectorise. Some code paths (e.g. he mentions md5) will not be vectorised, and so there is no speed increase in that case.

The reason why 400% is spoken of as the minimum increase is that with Altivec you can work on four 32-bit quantities at a time, as opposed to one at a time.

---

### Post by ssam on 2005-02-26
something to look forward to then  :smile: 

ssam

---

### Post by Viro on 2005-02-27
[QUOTE=toojays]

The reason why 400% is spoken of as the minimum increase is that with Altivec you can work on four 32-bit quantities at a time, as opposed to one at a time.[/QUOTE]

If that is the case, how is it possible to get a anything more than a 400% increase?

My personal experience with GCC 4.0 (built from source) is that it generally speeds things up by about 15% (Scimark and my own code). That's with the -ftree-vectorize flag that is supposed to turn on auto vectorization.

Don't get your hopes too high with regards to the promise of auto vectorization. It isn't a panacea.

---

### Post by toojays on 2005-03-01
[QUOTE=Viro]If that is the case, how is it possible to get a anything more than a 400% increase?
[/QUOTE]

One way would be if you were operating on 8x16-bit values, or 16x8-bit values.

I haven't played with GCC 4 yet. Of course it's not a panacea. Vectorisation at the compiler level is still relying on the data being laid out in a way which can be easily vectorised. There are many different patterns which could potentially be vectorised, and GCC 4.0 doesn't know them all. But it is going to be a lot easier for a developer to get good performance gains from Altivec if the compiler can do some of the boring work.

The documentation at developer.apple.com is very good for people who want to get an understanding of the capability of Altivec.

---

