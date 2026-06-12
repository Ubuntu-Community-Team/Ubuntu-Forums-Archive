---
title: "Mapping images"
date: 2009-02-11
forum: Art &amp; Design
---

### Post by VOLKOV9 on 2009-02-11
Hey.

So I don't know what I'm doing as far as graphics design.  But let's say I have an image - and let's say it's square in shape for simplicity.  And furthermore, I have a (bijective, for simplicity) function that maps a square to a square, say f(x,y)=(x',y').  How do I tell my computer to make a new image by sending my original image through this function?  i.e., make the image that, at coordinate (x',y'), is the same color as the original image at coordinate (x,y).

For instance, f(x,y)=(y,x) would flip the image about a diagonal (but I want to generalize this for any nice f).

I'm not so much asking for a complete walkthrough - more to be pointed in the right directions.  What sort of applications do I need to use / what do I need to learn?  I could do it in C if I knew how the computer translates images into .jpgs or whatever format is the simplest.  Are there other (/better) ways?  Is Gimp capable of this if I learn how its script-fu works?

Thanks a lot, guys.

---

### Post by AJB2K3 on 2009-02-12
Gimp should be able to this via scripts but you will need to look at the procedural data base ( hold all gimps internal scripting commands),
and look at how other scripts work.

[This page may be of use.]("http://www.ic.al.lg.ua/~ksv/gimpdoc-html/write_sc.html")

---

