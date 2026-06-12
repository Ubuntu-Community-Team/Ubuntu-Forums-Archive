---
title: "i'm an idiot: Need help with boot options on live CD"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by matoot on 2006-12-28
Is there a special way to enter boot options.  I enter irqpoll after boot: and nothing happens i just get another "boot:" prompt? I'm going nuts over here.....

---

### Post by po0f on 2006-12-28
matoot,

Are you booting from the live CD?  Hit F6; a bunch of kernel params should pop up, just append 'irqpoll' to the end of them.

---

### Post by matoot on 2006-12-28
thanks,

I'm booting from a liveCD.  When I enter irqpoll I get could not find kernal image....  I don't know what i.m doing.

---

### Post by po0f on 2006-12-28
matoot,

Did you leave a space between 'irqpoll' and the '--' at the end?

---

### Post by matoot on 2006-12-28
Thanks Po0f... I tried different things.  How should I enter the boot command

Boot: XXXXXXXX

Rob

---

### Post by K.Mandla on 2006-12-28
What about

```
linux irqpoll
```
?

Are you working off a guide or a howto?

---

### Post by po0f on 2006-12-28
matoot,

Boot the live CD.  When it gets to the menu, hit F6 before the timeout.  You should see a line that looks something like this (snipped):
```
[FONT="Courier New"]... root=/dev/ram rw quiet splash --[/FONT]
```
You want it to look like this:
```
[FONT="Courier New"]... root=/dev/ram rw quiet splash **irqpoll** --[/FONT]
```
After adding whatever kernel params you require, just hit enter and it will boot.

[EDIT]

Now that I think about it, the solution posted above by K.Mandla should work as well.

---

### Post by matoot on 2006-12-28
thanks for the help.  my machine must not be getting that far....

---

### Post by matoot on 2006-12-28
i'm downloading 6.10 to see if it will work....

---

