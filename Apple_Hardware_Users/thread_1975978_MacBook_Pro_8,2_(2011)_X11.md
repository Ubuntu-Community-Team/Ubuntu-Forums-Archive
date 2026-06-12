---
title: "MacBook Pro 8,2 (2011) X11"
date: 2012-05-08
forum: Apple Hardware Users
---

### Post by HarmlessSaucer on 2012-05-08
Hey guys, I've been following some peoples posts on this forum to try and get Ubuntu running on my MacBook Pro, but to no avail.

So far I've worked out that to get all the way to the command line:

[LIST]
Downloaded the X64 ISO - The i386 package gave me an error that it couldn't find the file system - something to do with SATA drivers methinks![/LIST]
[LIST]Changing the boot string to add "nomodeset" instead of "quiet splash"
[/LIST]

If I want X11 to start without giving an error on screens it cannot use I have to add:

```
Section "Device"
Identifier "Configured Video Device"
Driver "fbdev"
EndSection
```

But the issue is now the system just hangs on a **black screen**.  Any ideas?

---

