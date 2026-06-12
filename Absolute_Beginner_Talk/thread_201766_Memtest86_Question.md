---
title: "Memtest86 Question"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-22
I figured I'd check my memory with this test, and it ran 5 passes and ran an hour and a half before I finally stopped it. Anyone run this,and how many passes does it do on the default settings ?  Thanks

---

### Post by ajifans on 2006-06-22
I left it running on my dad's computer.  Came back two days later and it was still going!

I think just running it over night is the norm.

---

### Post by tribaal on 2006-06-22
Yes, memtest is an endless loop.
Baiscally you can consider you RAM safe if you successfully ran 1-2 passes. With 3 passes  you're really safe, and more than that is probably overkill.

Cheers

- trib'

---

### Post by Drakkor on 2006-06-22
Thanks guys, just was wondering,lol

---

### Post by az on 2006-06-22
Some memory faults are such that if you write to memory, they "fade" over a half an hour or so.  Memtest 86 can test for this as well as many other types of faults.  In some of the later tests, it writes a pattern, waits a half hour and then goes back to see if the same pattern is still there.  Rinse.  Repeat.

That's why it can go for so long.

If you are really paranoid, yes, test for as long as you possible can (days).  If you just bought some ram from ebay and want to see if it works, a few hours or overnight is great, too.  If you are paranoid about ram, don't get it on ebay...

---

