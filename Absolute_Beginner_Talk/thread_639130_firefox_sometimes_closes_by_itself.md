---
title: "firefox sometimes closes by itself"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-12-12
hello, i have a problem with firefox closing suddenly when i click on links from [http://adfasb.com/adfasb/11-19-07_ChristiesUTubeVideos.htm](http://adfasb.com/adfasb/11-19-07_ChristiesUTubeVideos.htm) for example. does anyone else have this problem?

---

### Post by daimaru on 2007-12-12
no mine does not crash.
but i had a similar problem a month back, which was related to flash content.

i deleted the flash plugin in ~/.mozilla/plugins
```
rm ~/.mozilla/plugins/libflashplayer.so
rm ~/.mozilla/plugins/flashplayer.xpt
```
went to a flash site and hit install when firefox asked me for needed extension. 

flash works fine, no more crashes for me. 
hope this works for you.

---

