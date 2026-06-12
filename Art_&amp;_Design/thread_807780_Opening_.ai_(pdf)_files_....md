---
title: "Opening .ai (pdf) files ... ?"
date: 2008-05-26
forum: Art &amp; Design
---

### Post by dbee on 2008-05-26
Hi Guys,

I can't seem to open a .ai illustrator (pdf) based file. The weird thing is that I can see the actual file contents via the thumbnail on my desktop. So it appears that something is able to view it.

When i try to open it with document viewer, the viewer opens, then 'loading..' then immediately shuts again. When i try to open it with inkscape i get 'inkscape encountered an internal error'.

When i download the ai2svg.py script for inkscape and run it. The script just hogs 99% cpu, then runs for 8mins+ without returning.

Help !

---

### Post by adewale on 2008-05-26
Thats very strange i know inkscare is able to open ai files. However try gimp

---

### Post by Jose Catre-Vandis on 2008-05-26
I work in Illustrator a lot on Windows.

I have no trouble opening pure .ai files with Adobe Reader 8, Document Viewer (Evince) and the Gimp. This is on an up to date Fiesty. Do you have Adobe Reader installed? Perhaps this will help?

---

### Post by dbee on 2008-05-26
The weird thing is that i can see the thumbnail of the image. But i can't actually open it ...

When i try gimp i get error ... 'portable document plugin cannot open file'

---

### Post by Xfcn on 2008-05-26
Are you trying to do a straigh "Open..." or are you doing an "Import..."?

---

### Post by dbee on 2008-05-26
Neither Import nor Open works for me ...

What could be the problem ?

---

### Post by hessiess on 2008-05-26
doze running it from the terminal shed any light on the problem?

---

### Post by dbee on 2008-05-27
Thanks dude,

Installing acroread from mediaubuntu and then running it under the terminal seems to work. I can't imagine why gnome won't open it. Ah well, it doesn't really matter though ...

```

DISPLAY=:0 && inkscape merit.ai

```

Cheers

---

