---
title: "8500GT, 6500GT: Turning auto-detection off"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by glaurens on 2008-01-23
I'm looking to run two plasmas and a monitor off of my 8500GT and 6500GT gpus. The thing that bugs me is that gutsy auto-detects displays, and thus, I can't start ubuntu while my monitor is switched to my other box or the plasmas are turned off (or at least as far as I could see).

Is there any way to make ubuntu start without auto-detecting displays and just to enable all ports as setup in the xorg file?

Tx

---

### Post by glaurens on 2008-01-24
Found the solution:

just add the line

Option "ConnectedMonitor" "CRT,CRT"


under the relative device section. Obviously if you are only running one monitor per GPU then use only one CRT.

G

---

