---
title: "config window size of root x-terminal-emulator?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by RgnKjnVA on 2007-11-23
looked at several threads on window resize but couldn't find one on configuring the x-terminal-emulator that the Root terminal uses. If I try adding --geometry WxH the setting is not implemented like it is when added to gnome-terminal windows. The man page on x-terminal-emulator references the --geometry config param though. ?!  :confused:

---

### Post by derby007 on 2007-11-24
Try : x-terminal-emulator -geometry 80x24+10+10 
Or mess around with these numbers.

---

### Post by RgnKjnVA on 2007-11-24
Awesome! Thank you. I've got those windows dialed in now.

---

