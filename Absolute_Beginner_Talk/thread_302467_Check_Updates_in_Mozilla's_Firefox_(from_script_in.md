---
title: "Check Updates in Mozilla's Firefox (from script installation) [Resolved]"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-11-18
Aysiu,
You gave me a link to a script that would allow me to load Firefox 2,0 in Dapper 6.06.  I have a question when I go to check for updates it is grayed out.  How do I enable this new Firefox program to check for updates when available or do I just run your script again when updates come out for Firefox.

---

### Post by aysiu on 2006-11-18
> **alienexplorers said:**
> Aysiu,
You gave me a link to a script that would allow me to load Firefox 2,0 in Dapper 6.06.  I have a question when I go to check for updates it is grayed out.  How do I enable this new Firefox program to check for updates when available or do I just run your script again when updates come out for Firefox.
You close Firefox.

Then press Alt-F2 and type ```
gksudo firefox
``` This opens Firefox as root. Check for updates and install them. Close Firefox again.

Open it again as a regular user.

More details here:
[https://help.ubuntu.com/community/FirefoxNewVersion#head-a48f484a5d03fb377e5f4ed0ff93a123f431c0a9](https://help.ubuntu.com/community/FirefoxNewVersion#head-a48f484a5d03fb377e5f4ed0ff93a123f431c0a9)

---

### Post by alienexplorers on 2006-11-18
Thanks for the reply.  I thought I messed something up when I installed the script.  Problem Resolved

---

