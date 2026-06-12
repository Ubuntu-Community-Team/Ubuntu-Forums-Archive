---
title: "Macbook Pro 5,5 Precise &quot;Unable to Enumerate USB Device on Port 4&quot;"
date: 2014-01-18
forum: Apple Hardware Users
---

### Post by Griffen_Schwiesow on 2014-01-18
Hello~

I have a Macbook Pro 5,5. I have a 500gb HDD with Mac OS X Mavericks and Ubuntu 12.04 installed.
For some reason, when booting to Ubuntu it takes forever to start.
Pressing the esc key shows me this message over and over:

```

unable to enumerate USB device on port 4
unable to enumerate USB device on port 4
unable to enumerate USB device on port 4
unable to enumerate USB device on port 4

```

When Ubuntu started, the keyboard and touchpad were both unusable. I plugged in a USB mouse and suddenly, both the touchpad and the keyboard are usable.
I used Terminal to run the command ```
lsusb
``` I found that the "Apple Internal Keyboard / Trackpad" uses port 4.

The same thing occurs during shutdown, ```
unable to enumerate USB device on port 4
```
I have updated everything and the computer runs perfectly except for this startup and shutdown.

I appreciate any help!

Thank you so much!

---

