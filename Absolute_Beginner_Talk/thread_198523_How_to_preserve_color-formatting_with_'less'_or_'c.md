---
title: "How to preserve color-formatting with 'less' or 'cat'???"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by xenblend on 2006-06-17
Hey all,

I do a lot of 'ls' commands and I pipe them through 'less' or 'cat' a lot.  I was wondering, is there any way to preserve the color-coding that bash does with 'ls' in the 'less' command so that directories stills how up as blue, sym links as green, etc.  Thanks!

:eek:

---

### Post by xenblend on 2006-06-17
In case anyone is interested the answer is 'ls -Al | less -R' to make less print colors.

---

### Post by xenblend on 2006-06-17
Sorry,

It's actually 'ls -Al --color | less -R'

XB

---

### Post by IYY on 2006-06-17
Thanks, this is something I'll be using often. :cool:

---

