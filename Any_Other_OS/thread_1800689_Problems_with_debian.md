---
title: "Problems with debian"
date: 2011-07-09
forum: Any Other OS
---

### Post by abnordude on 2011-07-09
I installed debian on my computer.
I also have compiz installed.

Compiz works perfetly.

The thing is that whenever I reboot or switch on the computer, compiz doesnt work.

Then I go to
Applications>>Others>>Compiz

And the effects are on.

But I cant do that every single minute I swith on my computer.

Help me.

---

### Post by An Sanct on 2011-07-09
This is a similar problem people have with Ubuntu (it being a Debian derivate, I think the procedures are the same...)

You should make compiz the default window manager, use

```
compiz --replace
```

This is a temporary script to activate compiz, it can be put into some startup code ...

The alternative is described [here]("http://ubuntuforums.org/archive/index.php/t-1757759.html") or [here]("http://forums.fedoraforum.org/showthread.php?t=239174") (I don't know which one will fire up Debian)

---

### Post by abnordude on 2011-07-09
> **An Sanct said:**
> This is a similar problem people have with Ubuntu (it being a Debian derivate, I think the procedures are the same...)

You should make compiz the default window manager, use

```
compiz --replace
```This is a temporary script to activate compiz, it can be put into some startup code ...

The alternative is described [here]("http://ubuntuforums.org/archive/index.php/t-1757759.html") or [here]("http://forums.fedoraforum.org/showthread.php?t=239174") (I don't know which one will fire up Debian)

I tried that, 
But I am losing the top bar, ie. the place where the close, maximize and minimize are present.

---

### Post by Stray Wolf on 2011-07-09
Maybe you should use emerald with compiz... works for me.  Though I did have to input emerald --replace once.  Compiz is supposed to run that command automatically.

---

### Post by abnordude on 2011-07-09
I dunno how but suddenly, when I rebooted the PC. 
The effects were still there.

i think the problem is solved.
Thanks everyone.

---

