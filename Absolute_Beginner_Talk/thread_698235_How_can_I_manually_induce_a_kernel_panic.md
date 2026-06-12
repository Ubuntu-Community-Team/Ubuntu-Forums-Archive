---
title: "How can I manually induce a kernel panic?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Starks on 2008-02-16
I'm bored and I want to see the Linux equivalent of a BSoD.

---

### Post by geenux on 2008-02-16
why do you want a kernel panic???
I think there's no way to induce manually.

---

### Post by Irihapeti on 2008-02-16
Well, you could make yourself a liveCD with some weird stuff in the GRUB menu.lst. I've had kernel panics a few times when playing with home-made liveCDs and I got the commands wrong. There was actually nothing much to see on the screen - only a bit of text: "Kernel panic" and then something else I don't remember. The keyboard LEDs kept blinking, and cntr-alt-del did nothing. I had to turn the computer off at the wall. Not really worth spending time doing, in my opinion.

---

### Post by PeterJS on 2008-02-16
You could write a kernel module that calls panic() when it's loaded, and then load it. It's pretty sure fire, but requires a bit of technical knowledge :)

---

### Post by sloggerkhan on 2008-02-16
kernel panic isn't that interesting. You just see a message at the end of a console 'kernel panic' and maybe 1 more line like 'fdsfdsflk not syncing' and then things are frozen and dead. Maybe if your unlucky a fan will be stuck at full speed or something.

---

### Post by peabody on 2008-02-16
> **sloggerkhan said:**
> kernel panic isn't that interesting. You just see a message at the end of a console 'kernel panic' and maybe 1 more line like 'fdsfdsflk not syncing' and then things are frozen and dead. Maybe if your unlucky a fan will be stuck at full speed or something.

Yeah, I agree, kernel panics are really boring.  If there's one thing Windows definitely does better than Linux it's spazing out in colorful ways.

---

### Post by yabbadabbadont on 2008-02-16
When at the GRUB prompt at boot up, hit escape for a menu (if it isn't already there).  Then highlight your normal boot entry and press 'e' to edit it (temporarily).  Now highlight the kernel line and press 'e' again to edit it.  Change the root=...  parameter to read root=/dev/null  Hit escape to exit edit mode and then hit 'b' to boot the modified entry.  Enjoy.

---

### Post by scorp123 on 2008-02-16
> **Starks said:**
> I'm bored and I want to see the Linux equivalent of a BSoD. There is a screensaver with the name "BSOD" (I am sure this is pure coincidence .... :) ) which has a nice collection of UNIX kernel panics .... I can make out at least one from Linux 2.4x, one from BSD, one really well done one (it looks about as ugly as the real thing!) from HP-UX and one which looks like it's from Tru64. And I think there are a few from MacOS X too. Try that one. 

It's funny as hell ... especially when Windoze users are watching. They go like "LOL dude, your machine has crashed ... " ... You just move the mouse and can say something cruel like "Nope dude, that's just the screensaver. We wouldn't know what a crash looks like if we didn't have this little screensaver to remind us ... "  :)

---

