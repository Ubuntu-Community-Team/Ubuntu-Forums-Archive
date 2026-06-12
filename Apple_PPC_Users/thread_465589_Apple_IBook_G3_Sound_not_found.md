---
title: "Apple IBook G3: Sound not found?"
date: 2007-06-05
forum: Apple PPC Users
---

### Post by Krammit on 2007-06-05
I just installed 7.04 and so far everything is great. Only problem I have is that when I try to turn up the volume it says "GStreamer plugins and/or devices found.", yet when I was using the live cd the sound worked perfectly. Anyone know how to fix this?

---

### Post by stmiller on 2007-06-06
In a terminal type

$ sudo gedit /etc/modules

and at the bottom of the list add

snd-powermac

save and close. Reboot and should work now.

---

### Post by Krammit on 2007-06-06
It workled! Thanks a buch. :)

---

