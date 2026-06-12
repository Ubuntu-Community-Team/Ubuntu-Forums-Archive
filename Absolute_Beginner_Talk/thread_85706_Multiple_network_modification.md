---
title: "Multiple network modification"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by search66 on 2005-11-03
Is there a way to modify Breezy to check for different network connections?  I have it installed on a laptop... at work, I use a proxy... at home... I don't... 

I'd like to modify the OS so it looks for either, and picks which is available.

Possible?

---

### Post by mlomker on 2005-11-03
I'd imagine that those proxy settings are saved to a file somewhere.  You'd have to find the file and then use some kind of script (perhaps **whereami**) to copy that file into place or delete it, depending upon where you are at.

---

