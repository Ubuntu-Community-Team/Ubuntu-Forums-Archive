---
title: "ndiswrapper question"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by gomezj00 on 2006-06-09
Hi,

I have a quick question.  When you run ndiswrapper -m, what file does it modify?  I'd like to know so that I could remove the entry.  Especially now that I'm no longer using ndiswrapper for my wireless card.  Any help would be greatly appreciated.  Thanks!

---

### Post by Burke on 2006-06-10
I'm pretty sure it creates the file /etc/modprobe.d/ndiswrapper , so you could delete that if you felt like it.

If you just want to get rid of ndis though, add "blacklist ndiswrapper" to a new line in the file: "/etc/modprobe.d/blacklist", then reboot. No more ndiswrapper.

---

