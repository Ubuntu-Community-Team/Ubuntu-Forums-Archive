---
title: "Firefox crashing"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by saadakhtar on 2007-01-17
my firefox started crashing for some reason. Is there anyway to daignose the main cause or some kind of utility to see what is actually happeining at the time of crash. the wierd part about my browser is that it does not even give me a error message. the browser would just close as if someone closed it by hitting quit. if i just restore my current browser session it crashes faster then if i start a new one but in either case the browser is unusable.
anyone else having the same problem. any fixes or patches. I am a edgy user so please advise accordingly.

---

### Post by taurus on 2007-01-17
Does it happen when you visit a site that requires flash 8?  Try to run it from a terminal to see  what's the problem is.

```
firefox
```

---

### Post by dca on 2007-01-17
In Edgy, after installing flash Firefox would close as soon as you opened it...
 
The fix (if I remember correctly) is to edit your : /etc/X11/xorg.conf file and change the screen depth to 24???  I think that's it...

---

### Post by phr0ze on 2007-01-17
Here is an answer that worked for me.

[http://www.ubuntuforums.org/showthread.php?t=286069](http://www.ubuntuforums.org/showthread.php?t=286069)

---

### Post by saadakhtar on 2007-01-17
guys,
thank you for the answers. i am going to try these methods out when i get home tonight.
will post the results once i try something.
appreciate the help.

---

### Post by old_geekster on 2007-01-17
> **saadakhtar said:**
> guys,
thank you for the answers. i am going to try these methods out when i get home tonight.
will post the results once i try something.
appreciate the help.
You may want to try "Swiftfox".  It has been far faster for me.  Probably at least twice as fast as FF2.0.0.1.:D

---

