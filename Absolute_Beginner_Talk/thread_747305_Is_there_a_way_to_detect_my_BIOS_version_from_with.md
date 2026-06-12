---
title: "Is there a way to detect my BIOS version from within Ubuntu?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-04-06
I am away from my computer today and am using VNC to use it by remote.  I am wanting to see if there is a way for me to get info about my BIOS while running Ubuntu.  Are there any utilities out there that can probe that kind of information?  My hope is I'll be able to find a way to update my BIOS from ubuntu...though that may not be possible.  We'll see...

---

### Post by wolfen69 on 2008-04-06
in terminal:
```
sudo dmidecode -q | less
```
bios version will be 3rd line down.

---

