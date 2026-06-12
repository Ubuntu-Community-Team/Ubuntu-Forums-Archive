---
title: "Difference between EXT3/Reiser/XFS?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-11-20
Difference between EXT3/Reiser/XFS?  What are the pros/cons?

---

### Post by aysiu on 2005-11-20
Wikipedia is your friend:
[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

---

### Post by ramdisc on 2005-11-20
Wikipedia is my friend if I am writing an essay, where I copy the article, change a few words, and shorten it.  But I am not.  I need someone to tell it to me in **plain English**.

Quoting from Wikipedia:

> Compared to ext2 and ext3 in 2.4, when dealing with files under 4k and with tail packing enabled, ReiserFS is often faster by a factor of 10–15.
I have no clue what 4k is.  Closest I come is knowing what a KB is.  I don't know what this "tail packaging" is or what it does.

That is just an example.  I, as well as others new to Linux, can read the article over and over again and have no clue what it is saying.  Like many computer articles.  It's full of terms newbies do not understand.

Basically, these computer articles are written **by** experienced Linux users **for** experienced Linux users.  Just as legal papers are written by lawyers for lawyers.  Anyone outside the practice of law have no clue what it is trying to say.

So would someone who has time on their hands please tell me what X can and cannot do that Y or Z can't, and vice versa?

---

### Post by steve.horsley on 2005-11-20
My understanding, in brief:

ext2 is pretty-much theoriginal Linux filesystem. 

ext3 is an extension of ext2 that adds journalling - it keeps a record of what it is about to write, then if the PC crashes while writing, it is generally possible to recover without massive file system corruption. The visible effect is simply less corruption upon power failure or crash.

reiser3 is also journalled. There are claims that it can be a lot faster if dealing with large numbers of small files. It is the one I always use (mainly because I started out with Suse, which defaults to reiser3), and has never let me down.

XFS is another file system. I know nothing about it.

In terms of what they can do, they are al the same except that ext2 isn't journalled, so is more likely to get corrupted during a crash or blackout. The arguments are all about performance, adn I gather there is no clear winner there.

---

