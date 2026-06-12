---
title: "Delay programs in Autostart?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by NikoC on 2007-01-16
Hi there, I was wondering if there is a way to 'delay' the start of programs placed in the Autostart folder (using KDE)? For example: I managed to install beryl but there is a problem with window frames flickering... killing and restarting emerald however fixes this issue... so I tried to write this small  .sh script that I put in Autostart. This script finishes before beryl and emerald even start so I was wondering if I could add a delay option (like 2s or something).

---

### Post by Obor on 2007-01-16
Here is a script I use for starting up conky. I think you just say "sleep #ofsecs" It should work the same in KDE.

ie. for conky it would be:
```
#!/bin/sh
sleep 10
conky
fi
```

---

### Post by NikoC on 2007-01-17
Thanks Obor, going to try it out... soon ;)

edit: worked fine, thanks

---

