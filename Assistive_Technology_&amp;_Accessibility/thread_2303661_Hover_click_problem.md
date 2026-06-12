---
title: "Hover click problem"
date: 2015-11-20
forum: Assistive Technology &amp; Accessibility
---

### Post by michael277 on 2015-11-20
I'm using Ubuntu version 12.04, and after logging out and back in to restart Firefox bacause it wasn't responding, the screen turn into a bunch of text, so I had to turn the computer off and back on. Once i had logged back in (again), I got some "internal error" messages or something like that. When i was done with that i noticed that hover click, which was supposed to be on, wasn't working, so i went to system settings, universal access, and it said hover click was on. So i turned it to off and, and it logged me out of my account. Now whenever I turn hover click to on, the box doesn't come up, and hover click dosen't work; and when I turn hover click off after turning it on, it logs me out.

---

### Post by michael277 on 2015-12-03
bump

---

### Post by buzzingrobot on 2015-12-03
Can't help with that specific hover click issue.  But, if you can recall, more info about what was displayed when the screen turned "into a bunch of text" and what those "internal error" messages said might help someone else resolve this.  Also, had you altered or updated the machine in any way prior to Firefox crashing?

You might try resetting and restarting Unity:

> sudo apt-get install dconf-tools

dconf reset -f /org/compiz

... and reboot.

---

