---
title: "Decreasing resolution"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Crossbow on 2007-04-28
My screen resolution defaults to 1400x1050, which on my my monitor is too small to see anything. I want to decrease it to 1280x1024, but when I do that it just shrinks the whole desktop so everything is still just as small! How do I get it to fill the screen at that resolution? I have looked in all the "preferences" and "administration" options I can think of. I assume it's something I need to do in a terminal, but I have no idea what.

---

### Post by Slackpacker on 2007-04-30
Reconfigure the X server to add the correct resolution.  Just use the defaults for stuff you're not sure about.
The command is [B]sudo dpkg-reconfigure xserver-xorg
[/B]
Restart X when you're done.

---

