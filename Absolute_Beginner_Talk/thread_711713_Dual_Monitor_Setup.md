---
title: "Dual Monitor Setup"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by rfaith88 on 2008-02-29
I have a single ATI Radeon X600 Card, and it has a DVI and an analog port.  Right now, I have two monitors hooked up to it, but the images are cloned on each.  How can I extend my desktop so that I can drag windows from one monitor to the next?

I have tried to use the "screens and graphics" tool, but it is only showing me "screen 1" and not my second.  Is there a special way that I need to enable my second monitor?

---

### Post by Crooksey on 2008-03-01
I think if you run..

```

$ man aticonfig
```

It will list the commands you need, been a few years since I ran ATI and dual head, think the command is something like...

```

$ sudo aticonfig --dtop=horizontal
```

---

