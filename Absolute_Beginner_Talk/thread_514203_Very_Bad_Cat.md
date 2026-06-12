---
title: "Very Bad Cat"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by DrTaylor on 2007-07-31
I booted up my computer and went to do laundry, and when I came back the cat was sitting on my keyboard and the computer:-({|= was doing something funky I'd never seen before. I only caught a glimpse and then it booted up normally, but I can't install any software or even updates. When I try, I get a message that says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I try to run dpkg --configure -a, and it says:

dpkg: requested operation requires superuser privilege

Can someone please tell me what she pressed?

As an aside: does anyone know if there is a version of that catpaws program (you know, the one that just makes your computer ignore gibberish) for linux?

---

### Post by be4truth on 2007-07-31
try 

```
sudo dpkg --configure -a
```

in a shell. Then take care of your cat.

---

### Post by st33med on 2007-07-31
Try:
```
sudo dpkg --configure -a
```

And punish that darned cat.

Speaking of which, [TEH CUTEST CAT IN TEH WRLD!!!11!!!!]("http://www.youtube.com/watch?v=ewS_nDdwJsY&mode=user&search=")

Dang, you beat me to it. Competition for the first to advise a person is strong here!

---

### Post by DrTaylor on 2007-07-31
Thanks, that's that fixed.

What to do about the cat, I'm really not sure. I can't keep her off the computer all the time.

---

### Post by p_quarles on 2007-07-31
> **DrTaylor said:**
> Thanks, that's that fixed.

What to do about the cat, I'm really not sure. I can't keep her off the computer all the time.
One thing you could do is lock the screen when you're not using it. That way, she can press all the keys she wants and it won't do anything. Unless she knows your password, of course. :)

---

### Post by be4truth on 2007-07-31
What about hiding the mouse?

---

