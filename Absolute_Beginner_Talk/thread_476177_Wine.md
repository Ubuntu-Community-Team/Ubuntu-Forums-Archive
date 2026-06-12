---
title: "Wine"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by rex66 on 2007-06-16
I have installed wine in an attempt to use a small windows based application. I have extracted the .exe file to a folder I created on my desktop. This is where I am stuck. How do I get wine to run this program? I've opened the wine file browser but can do little more than look at the file?

Thanks
rex66

---

### Post by yabbadabbadont on 2007-06-16
[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)

Specifically: [http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index)
[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)
and [http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)

Short answer: In a terminal window```
cd ~/Desktop/folder-you-created
wine name-of-program-you-extracted.exe
```
:D

---

### Post by rex66 on 2007-06-16
thanks yabba.....but I'm getting a module not found message. Does this mean that my obscure little program is just compatible with wine?

---

### Post by yabbadabbadont on 2007-06-16
What does the wine application database have to say about your application?  You did look it up when you came to the point in the wine howto that told you to do so didn't you...   ;)

---

