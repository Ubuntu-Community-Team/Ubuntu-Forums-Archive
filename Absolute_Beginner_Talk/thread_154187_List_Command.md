---
title: "List Command"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by maxbaggi on 2006-04-02
What is the command to list the filename, size, type and meta info (Length, Resolution, Frame Rate, Video and Audio Codec) in a directory containing video clips?

---

### Post by maxbaggi on 2006-04-04
bump

---

### Post by Mustard on 2006-04-04
[QUOTE=maxbaggi]bump[/QUOTE]

```
file <filename>
#example below 
#file somerandomvideo.avi
```

---

### Post by maxbaggi on 2006-04-05
Hi Mustard, thanks for replying :-D
I entered "file *.*" in the terminal. It displayed the meta info of all the clips in the folder... but it didn't list the size and modified/accessed date.  Also the output of the command was a little difficult to follow because it was not aligned properly.  Is it possible to neatly align it into columns... kind of like ls -l does... and would it possible to rearrage the columns... I want it in the following order.
Filename     Size     Length     Resolution     Frame Rate     Audio/Video Codecs     Date

Thanks :-D

---

### Post by Mustard on 2006-04-05
[QUOTE=maxbaggi]Hi Mustard, thanks for replying :-D
I entered "file *.*" in the terminal. It displayed the meta info of all the clips in the folder... but it didn't list the size and modified/accessed date.  Also the output of the command was a little difficult to follow because it was not aligned properly.  Is it possible to neatly align it into columns... kind of like ls -l does... and would it possible to rearrage the columns... I want it in the following order.
Filename     Size     Length     Resolution     Frame Rate     Audio/Video Codecs     Date

Thanks :-D[/QUOTE]

It's probably beyond my knowledge how to succesfully do what you are wanting to do.  I imagine someone with some scripting knowledge could do it.

---

### Post by Madpilot on 2006-04-05
There are a number of other options for "ls" that might get some of what you need - try "man ls".

There might also be options for "file" you could check out - "man file", of course.

---

