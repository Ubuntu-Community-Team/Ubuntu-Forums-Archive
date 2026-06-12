---
title: "What is typical for number of re-writes to DVD +RW?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by bhold on 2008-04-04
Just curious how many times is typical for being able to re-write a DVD +RW? I backup my system by creating a tar.gz file then using Gnome Baker to write the tar.gz to DVD +RW and usually get between 15 and 30 re-writes. Any time after that - thats all folks - the DVD becomes unreadable and won't even mount.  Is this typical or might this indicate I have a DVD drive hardware problem?

---

### Post by kevin11951 on 2008-04-04
> **bhold said:**
> Just curious how many times is typical for being able to re-write a DVD +RW? I backup my system by creating a tar.gz file then using Gnome Baker to write the tar.gz to DVD +RW and usually get between 15 and 30 re-writes. Any time after that - thats all folks - the DVD becomes unreadable and won't even mount.  Is this typical or might this indicate I have a DVD drive hardware problem?

[http://en.wikipedia.org/wiki/DVD%2BRW](http://en.wikipedia.org/wiki/DVD%2BRW)

> DVD+RW supports random write access, which means that data can be added and removed without erasing the whole disc and starting over **(up to about 1000 times)**. With suitable support from the operating system, DVD+RW media can thus be treated like a large floppy disk, in contrast to DVD-RW which must be erased before re-writing can take place.

---

### Post by The Titan on 2008-04-04
> **bhold said:**
> Just curious how many times is typical for being able to re-write a DVD +RW? I backup my system by creating a tar.gz file then using Gnome Baker to write the tar.gz to DVD +RW and usually get between 15 and 30 re-writes. Any time after that - thats all folks - the DVD becomes unreadable and won't even mount.  Is this typical or might this indicate I have a DVD drive hardware problem?
i have had DVD-RW's start corrupting bits and pieces after like 10 times of erasing parts of it.. But i buy cheap blank media =/

---

### Post by logos34 on 2008-04-04
Make sure you're not **reformatting** the dvd+rw every time--you merely overwrite the existing data.

> It was observed that excessive reformats can render DVD+RW media unusable already after 10-20 reformats. It appears to be a firmware deficiency, not some common media defect [at least it was perfectly possible to salvage the media in a unit of different brand], but I don't recommend [enforced] reformat in either case.

Note that re-formatting procedure does not substitute for blanking. If you want to nullify the media, e.g. for privacy reasons, do it explicitly with 'growisofs -Z /dev/scdN=/dev/zero'. Otherwise just write over previous recording as it simply wasn't there, no re-formatting is required.
Source: [http://fy.chalmers.se/%7Eappro/linux/DVD+RW/](http://fy.chalmers.se/%7Eappro/linux/DVD+RW/)


---

### Post by bhold on 2008-04-04
> **logos34 said:**
> Make sure you're not **reformatting** the dvd+rw every time--you merely overwrite the existing data.

What I do is run Gnome Baker, drag the tar.gz file to the Data DVD area, and burn. No reformat. After (at most) 30 backups, the DVD is toast.

---

