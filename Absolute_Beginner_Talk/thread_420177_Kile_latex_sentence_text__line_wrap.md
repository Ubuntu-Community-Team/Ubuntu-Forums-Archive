---
title: "Kile latex sentence text  line wrap"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-04-23
Hi,

For some reason Kile does not show all sentences numbered but showed ome of them with "arrow" (please see attachment, I marked circle). This is not good since when you made a mistake, say at the line of "arrow", you will not have any info (line number) at which line the mistake is at. It gets more annoying when Kile makes say 5-10 consequtive lines with arrows instead of numbering the lines, then finding error becomes more difficult.

Is there a way to correct it? I mean I dont want any arrow but show all line numbered. Is it trivial?

best
findik

---

### Post by nanotube on 2007-04-23
hi
arrows just show the line wraps
the line count only counts full lines - lines that end with a linefeed.
so, in your screenshot, line 3 is just one line - it's just wrapped on the screen for your convenience, so that you don't have to scroll horizontally to see all of it.

if you want to stop seeing the arrows, just turn off wordwrap. of course, then you will have to scroll horizontally to see the full line...

---

### Post by findik1 on 2007-04-23
thanks
so I want word wrapping so that I dont scroll horizontally. But at the same time I want automatically number each line, it does not have to end that sentence. (Like 'Winedt" in windows). Is it possible?

---

### Post by nanotube on 2007-04-23
not as far as i'm aware... maybe someone else knows different. 

but in the meantime, if you want to track down the mistake, just break the line into several manually, and recompile, and see where the error is. :)

---

