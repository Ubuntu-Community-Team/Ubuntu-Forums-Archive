---
title: "wine question: &quot;Run-time error 438&quot;"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by brn on 2007-02-17
Wine works great for several of my DOS/Windows applications  but one in particular produces this message:  
> Run-time error 438
Object doesn't support this property or method

I have tried it with the target package locally (~/.wine/drive_c/...etc...) and in the FAT32 partition I use to communicate across platforms with WinXP.  (This works with XP.)  I'm using what I think is the latest release of wine; 0.9.30.  Before trying to report a bug on the wine website, i wonder if anyone in this forum can explain "Run-time error 438" and suggest a possible work-around.  --Thanks--

---

### Post by jpeddicord on 2007-02-17
I've never seen a Run-time in Wine itself, only in the Windows programs that it can run. It almost seems like a bug in that software. But, if it works on the XP partition, chances are that it is in fact Wine. You could report a bug if you want, but be prepared to provide a debug backtrace. It might even get fixed in the next version of Wine.

---

