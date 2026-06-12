---
title: "Extremely high cpu usage... yet nothing's using it."
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Exershio on 2008-01-04
I'm running Ubuntu 7.10 on the following system:
2.0ghz P4 Processor
768mb DDR PC2100 RAM
Radeon 9550 AGP 4x 256mb
250gb EIDE HDD

My CPU usage is constantly at 90-100%, even when I'm doing nothing. However, when I open up my processes tab, nothing is consuming more than 10%. When I first installed Ubuntu like.. 20 minutes ago, my CPU usage would sky rocket just by clicking a button, moving the mouse, scrolling a website, etc. I have installed the restricted drivers as well, so I don't see what's causing this.

Can somebody help me out?

Here's some images:

[img]http://img262.imageshack.us/img262/2866/screenshotsystemmonitorjc1.png[/img]
[img]http://img91.imageshack.us/img91/232/screenshotsystemmonitorup2.png[/img]

---

### Post by Hallvor on 2008-01-04
Try something else: Launch the terminal and type ```
top
```

---

### Post by RomeReactor on 2008-01-04
Hi. In System Monitor, go to "View" and select "All Processes". Then sort them out by **% CPU** and see who's the culprit (probably Java or Flash).

---

### Post by ukripper on 2008-01-04
I guess culprit could be Youtube running FLV

---

