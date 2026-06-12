---
title: "Where did it go?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-10-20
I spent several days trying to get DVD backup software to work. We won't go there. :-D However! I started out 4 days ago with 19 plus gigs of free space and today I started out with 2.

I've poked around with Nautilus and recovered about 3 gigs – they were aborted copies of a dvd. I'm sure that this is where all the space went, there must be parts of the dvd all over.

How would I search for files by file size? In windows I used a gui utility called Power Desk that had a thing called size manager  it listed the largest files at the top of a tree view. Does anyone know of a similar thing for Linux?

---

### Post by toxygen on 2006-10-20
one way is:

```
find / -type f -size +10000k
```
if you want to find files bigger than 10 megabytes.

also the other way could be
```
du -aS | sort -r -n | less
```
which is rather chaotic and harder to understand :)

---

### Post by whein on 2006-10-20
There is a program called baobab that graphically displays how big each directory/file is relative to each other.  May not do exactly what you want, but will definitely get you started.  I think it is in the default install of 6.06 but you may have to turn on the icon using the alacarte menu editor.  If it isn't installed, you can find it in the repositories.
-Will

---

### Post by podunk on 2006-10-20
Thank you both! :-)

---

