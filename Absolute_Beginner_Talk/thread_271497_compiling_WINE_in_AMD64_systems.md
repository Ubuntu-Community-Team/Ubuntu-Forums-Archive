---
title: "compiling WINE in AMD64 systems"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-04
Hello!
Yet another question from me (a newbie who is still learning Ubuntu). I was reading the thread located [here]("http://www.ubuntuforums.org/showthread.php?t=167765") (the thread describing the compilation of wine in a X64 system architecture), and I have had no problem with what it asks until it reaches the wget commands. It says to use wget -c in the following way:

```


wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34-dev_3.4.1a-1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf2_1.4pre.20030402-1.1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf-dev_1.4pre.20030402-1.1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libx11/libx11-dev_6.2.1+cvs.20050722-8_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext6_1.0.0-0ubuntu4_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.0-0ubuntu4_i386.deb


```

However, it says that those sites are no longer valid. Obviously, these files have been upgraded. However, going to the index containing these files [ http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/ ]("http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/"),
shows a lot of files. I don't know which ones to use. I'm asking which ones I should now use instead. I know it takes a little bit, but I would really appreciate it if someone could help me out. Thank you so much if you can help here (I need to get Flash enabled).

---

### Post by shanepardue on 2006-10-05
just add this to your /etc/apt/sources.list

"deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main"

then "sudo aptitude update" and "sudo aptitude install wine". now you got the latest wine.

**edit - misread..didn't see the 64-bit architecture..my bad!

---

### Post by pay on 2006-10-05
They don't make 64bit versions of wine so using the repository won't work. Just install the deb using the --force-architecture option.

---

