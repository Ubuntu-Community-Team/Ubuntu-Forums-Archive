---
title: "Firefox crashes randomly, where to start trouble shooting?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by woohhaa on 2007-07-07
I'm running feisty fawn 7.04 and Firefox crashes randomly, where do I start trouble shooting?

This is my first go around with linux and I'm not seeing any info that just screams this is the problem in the system log.

Any advice would be much appreciated. 

Cheers.

---

### Post by AlexenderReez on 2007-07-07
open firefox using terminal....use it...see the error......

---

### Post by woohhaa on 2007-07-08
Thanks for the quick reply reez0105. 

I opened the terminal, typed in firefox, it opened crashed after a few minutes, no error messages in terminal window. Is there a command I need to use to get the error log?

---

### Post by Moop on 2007-07-08
Many firefox crashes are caused by a corrupted profile. You can create a new profile and see if that solves the problem. 
```
firefox -profilemanager
```

---

### Post by aysiu on 2007-07-08
That's weird. There's usually an error message. Can you try [this](http://ubuntuforums.org/showthread.php?t=103930&highlight=corrupt+profile) and see if it still crashes?

---

