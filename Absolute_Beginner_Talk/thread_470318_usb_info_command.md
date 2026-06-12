---
title: "usb info command"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2007-06-10
im attempting to get a usb device working (a palm pilot), however at this point, i am unsure whether my computer even recognizes its connected at all.  is there a command that will return info about the current usb states, and/or what they are currently connected to.

perhaps kinda like lspci but with further information about current status.

thanks!

---

### Post by starcraft.man on 2007-06-10
```
lsusb
```

That is the basic command. If you want to know all the modifiers do:

```
man lsusb
```

And if you want more info on each USB port, do:

```
lsusb -v
```

That should be it. Best of luck with it. :)

I know nothing about palm's so can't help you further... unless you have general questions.

---

