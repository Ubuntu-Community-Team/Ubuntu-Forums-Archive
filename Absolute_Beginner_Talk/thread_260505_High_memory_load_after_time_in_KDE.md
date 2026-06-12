---
title: "High memory load after time in KDE"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-18
Hey everyone. Just need a little help about understanding the memory load in kde. When I first log in it has a small load around 250mb or so. But, after I open some windows and some media players, then close them, my memory remains around 700-800. I dont know what is taking all the memory. I closed all the applications that were open before. Anyone know what Im talking about? :D  :confused:

---

### Post by croak77 on 2006-09-18
What does 'free -m' from a terminal show you? Are sure your memory is not cached?

---

### Post by jordanmthomas on 2006-09-19
In Linux, nearly all your memory is used commonly.  This is no big deal, though, as it is just keeping extra stuff around in case you need to get it again (because RAM is faster than your hard drive).

If you need the memory for a program, the extra stuff will get moved over to the swap.  Anyway, when you run *free* from a terminal like croak77 suggested, look at the **( - / + ) buffers / cache** to see how much RAM you are "actually" using.

---

