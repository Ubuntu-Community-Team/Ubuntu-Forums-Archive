---
title: "avidemux problem with psp"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by siongz on 2008-03-09
hi... i have a problem with my avidemux program.
when i convert an avi format video to psp H264, which took me about 5 hours, i cannot open the file, it says no application is suitable to handle this kind of file. when i try to check the file type, its unknown.
could anyone help me on this??? thx

---

### Post by estaticd on 2008-04-14
The output file is meant to be played on a PSP game system.  Best of luck playing it on your computer, but I would try using VLC.  When you save the file, do you put any extension on it?  like .avi or .mpg?

Need a quick quide?  See here or search for PSP:
[http://ubuntuforums.org/showthread.php?p=3709311](http://ubuntuforums.org/showthread.php?p=3709311)

> **wickwire said:**
> Same problem here, solved it using this "recipe", hope it works for you:

```
Avidemux 2.4:

1- Load input file with "Open"
2- Select "Auto" -> "PSP (h.264)"
	2.1 - Select "PSP" instead of "PSP fullrep" leaving ratio as is
3- Video section (on the left) choose MPEG-4 ASP (lavc)
4- Save file with <may_be_original_filename>.MP4
5- Once finished, copy the MP4 file to the "VIDEO" directory in the mem stick
```

PSP 3.71-M33 update 2

This seems to be the only working combination of parameters for me.

---

