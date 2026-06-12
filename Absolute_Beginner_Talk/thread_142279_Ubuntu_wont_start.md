---
title: "Ubuntu wont start"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by t3h_mounty on 2006-03-10
Like the title says, I can't start Ubuntu. I had it all nice and good working, and now it wont start. Dunno why. I haven't changed anything that I can think of.

from the grub menu, I select the default Ubuntu.

Ubuntu loading screen starts up, goes for a few seconds, then it switches to some command line looking screen.

displays:

```
Unable to find volume group "Ubuntu"
ALERT! /dev/mapper/ubuntu-root does not exist. Dropping to a shell.
```

if anyone can tell me what's going on, that would be a real help. Much thanks.

---

### Post by rboss on 2006-03-10
Apparently there is a problem with the raid-configuration (Ubuntu installs the raid-support by default)

Have you created a special raid-volume and installed ubuntu on it?

Can you show the content of /var/log/dmesg?

---

### Post by t3h_mounty on 2006-03-10
no. no I can't.
regular bootup all I get is the message previously described, and I can't type anything, navigate anywheres... etc.

recovery bootup, yay for command lines! unfortunately, there is no "log" folder inside my "var" folder. There's a "lock", but that's not quite what we're looking for. so... yeah.

I'm kinda hoping there's some way to fix this without reinstalling ubuntu, I just got everything configured right and I'd really rather not have to do it again. :(

If I created a special raid-volume and installed ubuntu on it, I wasn't aware of the fact. I just installed ubuntu with pretty much only the default settings.

---

