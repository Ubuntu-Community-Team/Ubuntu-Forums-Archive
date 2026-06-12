---
title: "Shutdown sequence hangs for a bit"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by sleepytom on 2007-01-16
Lately when I shut down my Ubuntu installation I get part way through the shutdown and the sequence drops to a command prompt for about a minute. The command prompt is not active; it does not allow any commands to be entered. After a minute or so the Ubuntu splash appears again, which shows me the rest of the shutdown sequence. The first item that gets displayed when I get back to the normal sequence is something like "Unmounting peripheral devices". This didn't use to happen - could it have something to do with setting a mount point for my daughter's ipod? Any other ideas about how to prevent this long delay in shutting down?

Thanks

---

### Post by sleepytom on 2007-01-17
Okay, I figured this out on my own and here's the deal. If I power down my VmWare virtual machine before shutting down the computer, the shutdown sequence goes quickly and smoothly without dropping to a command prompt. So I think Ubuntu is just powering down the virtual machine when this happens.

---

### Post by 09adi09 on 2007-01-17
Is there a way to put the start up prompts we see into a text file?

---

