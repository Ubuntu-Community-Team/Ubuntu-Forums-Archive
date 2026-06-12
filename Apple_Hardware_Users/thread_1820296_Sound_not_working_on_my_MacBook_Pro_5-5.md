---
title: "Sound not working on my MacBook Pro 5-5"
date: 2011-08-07
forum: Apple Hardware Users
---

### Post by slugs on 2011-08-07
Hello. I've just installed Lucid Lynx on my MacBook Pro 5-5 and the sound is not working. I've followed the instructions at [https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound) and still have had no success so far. I've been trying to find a solution for days.

---

### Post by ~!geek!~ on 2011-08-07
Lucid lynx guys often facin this issue. I still don't know the reason of this problem, but you may take a look at this thread:  [http://ubuntuforums.org/showthread.php?t=1804227](http://ubuntuforums.org/showthread.php?t=1804227)

---

### Post by fdrake on 2011-08-07
Can you output
```
lspci -vvv | nl | grep Audio
```

---

### Post by slugs on 2011-08-08
The output is

```
80	00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
```

---

### Post by slugs on 2011-08-08
I've just upgraded to Ubuntu 10.10 and sound is still not working.

---

### Post by slugs on 2011-08-08
I finally solved the problem by unmuting front speakers in alsamixer. :)

---

### Post by gz841203 on 2011-08-09
I can use this on my apple computer very well!

---

