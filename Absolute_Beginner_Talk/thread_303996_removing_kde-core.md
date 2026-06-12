---
title: "removing kde-core"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-21
Read on psychocats that kde-core went faster than kubuntu-destop. didn't like how it came out, have taken to xubuntu in a big way, and now want to get rid of kde-core in its entirety. should be a giant chunk of code to paste in somewhere eh?

---

### Post by Bachstelze on 2006-11-21
Did you install kde-core with apt-get or aptitude ?

---

### Post by leetrefz on 2006-11-21
with attitude.

---

### Post by leetrefz on 2006-11-21
the second one.

---

### Post by twrock on 2006-11-21
Hey, that makes me wonder about something. Is using Synaptic the equivalent of apt-get or aptitude?

---

### Post by Bachstelze on 2006-11-21
**leetrefz** : then just do *sudo aptitude remove kde-core*.

**twrock** : basically, yes but there are a few differences - for example, aptitude remembers dependencies, which can be useful in cases like lettrefz'.

---

### Post by leetrefz on 2006-11-21
ok, not exactly a giant chunk. 
cheers. 

I'll stop asking stupid questions one of these days.

---

### Post by Bachstelze on 2006-11-21
Actually, if you had used apt-get instead, it would've been a "giant chunk", since you'd have neeeded to remove each and every package separately.

---

### Post by leetrefz on 2006-11-21
but wait that only removed 41kb. oh god. I'm going to have to get the xubuntu iso. nooooooooo

---

### Post by twrock on 2006-11-21
> **HymnToLife said:**
> **twrock** : basically, yes but there are a few differences - for example, aptitude remembers dependencies, which can be useful in cases like lettrefz'.

So it sounds like there are more differences than I had thought. I was basically trying to determine if using Synaptic to install packages would result in exactly your point above: all of the dependencies would be remembered vs. apt-get. But maybe it's not that simple.

---

