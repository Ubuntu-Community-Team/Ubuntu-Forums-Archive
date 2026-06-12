---
title: "Flash9 on 64-bit"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Locutux on 2007-12-04
Hello everybody.

I have a problem with Ubuntu 7.10, for 64-bit PC. I cannot view certain flash stuff, like MySpace players, etc.

I have flushplugin-nonfree and gnash installed, but still this ain't working. I tried couple suggestions from the Ubuntu forum, like uninstalling Firefox, flushplugin-nonfree & gnash and re-installing them, but still can't get the damn .swf player to work.

I even tried installing flash player from the terminal, but it seems that I need 32-bit libs. I don't know where to get them or how to install them. I tried searching the Ubuntu Forums, but got nothing useful. I'm sure it's there, but I guess I cannot find it. :S
Here's what I get:

```

ERROR: Your architecture, \'x86_64\', is not supported by the Adobe Flash Player installer.

```

I would appreciate your help.
Thank you,
Locutux

---

### Post by Locutux on 2007-12-04
Anyone? :S

---

### Post by crjackson on 2007-12-04
> **Locutux said:**
> Anyone? :S

Open up a terminal and type:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Locutux on 2007-12-04
Thanks.

This is weird. I tried this at least two times, and it didn't worked. :) 
Now it works perfectly fine. 

Ubuntu works in mysterious ways. :P

Thanks again.

---

### Post by crjackson on 2007-12-04
> **Locutux said:**
> Thanks.

Thanks again.

No problem...

Please go to the top right of the post, select thread tools and mark this thread as SOLVED.

---

