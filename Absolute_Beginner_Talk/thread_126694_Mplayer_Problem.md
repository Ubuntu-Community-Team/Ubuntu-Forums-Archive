---
title: "Mplayer Problem"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by PENG on 2006-02-07
When I play movie with format of rm, I meet error that it cannot find codecs matching selected video format 0*30345652.
after checking the tools , I find that video codecs is null.
Could anyone tell me which is the seleted term for Mplayer.
Thank you.

---

### Post by rmjokers on 2006-02-07
I think you are looking for the w32codecs package which will give you codecs to play restricted video formats.  See the wiki for further info:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by PENG on 2006-02-07
[QUOTE=rmjokers]I think you are looking for the w32codecs package which will give you codecs to play restricted video formats.  See the wiki for further info:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")[/QUOTE]
I have already installed w32codecs. 
All the depended packages provided by aptitude have been installed.

---

### Post by PENG on 2006-02-07
yeah!!!
it is been solved...
replace former w32codecs packages of new versions with w32codecs_20050412-0.0_i386.deb..
All are solved...

---

