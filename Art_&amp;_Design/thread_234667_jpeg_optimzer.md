---
title: "jpeg optimzer"
date: 2006-08-11
forum: Art &amp; Design
---

### Post by beercz on 2006-08-11
Hello

Not entirely sure if this is the right forum, if not then mods please move it to the relevant one.

I have several jpegs that need to be reduced in size.  Anyone know of a utility that will do this for me in one go rather than having to do one at a time in something like the Gimp?

I have several hundred jpeg images to process.

Thanks in advance.

---

### Post by gThree on 2006-08-11
gimp has a "batch" mode ... haven't tried it, but you might want to google it before you write gimp off ... something like:
```
gimp -b [commands]
```where commands are found in Xtns >> Procedure Browser.

Otherwise, there's always Imagemagick's "convert" command.  Rough example:
```
convert -quality 60 orig.png output.jpg
```
Not sure how they compare, but one or the other should do the trick.

---

### Post by beercz on 2006-08-12
Thanks gThree

Didn't know the Gimp had a batch mode - I'll look into that!

I have just installed imagemagick - do I shall delve into this too.  It appears that I may be reaching a solution to my problem.

Thanks again gThree.

---

### Post by beercz on 2006-08-13
Solved it - it was quite easy in the end.

I installed imagemagick and then went to the directories containing my image files (using terminal).

Then I used the mogrify tool thus:

> mogrify -resize 75% *.jpg

Job done :-)

Thanks once again gThree.

---

### Post by commodore on 2006-08-13
Can you do something like that in Windows this easily? I don't think so! Linux rules! :D

---

### Post by beercz on 2006-08-13
> **commodore said:**
> Can you do something like that in Windows this easily? I don't think so! Linux rules! :D

Don't know, don't care!! :-) (about doing the same task in Windows I mean)

---

