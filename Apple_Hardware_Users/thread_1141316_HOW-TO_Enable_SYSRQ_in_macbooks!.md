---
title: "HOW-TO: Enable SYSRQ in macbooks!"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by volanin on 2009-04-28
This how-to will allow you to remap the SYSRQ key, that is absent in macbooks,
to any other key on the keyboard, allowing you to REISUB properly in the
moments of hard crashes.


[i][b][color=red]_Warning_: To use this tip you MUST recompile your kernel.
You can use either the vanilla source or the ubuntu source.[/color][/b][/i]


**_Step 1_. Edit the file include/linux/input.h**

Search for the following line:
```
#define KEY_SYSRQ               99
```

And replace the number 99 with the number of any other key.
I personally prefer 126, the useless right apple key.
So my edited line looks like:
```
#define KEY_SYSRQ               126
```


**_Step 2_. Enable Magic SYSRQ**

Be sure to enable the Magic SYSRQ in:
```
[*] Kernel hacking -> Magic SysRq key
```


**_Step 3_. Recompile the kernel and enjoy**

Just recompile the kernel as usual.
Next time you boot, hold ALT + NEW_KEY and press REISUB slowly!
:)

---

### Post by volanin on 2009-04-28
Weird.
After testing a little more I found out that this does not work in X.
You must access a terminal (CTRL+ARL+F1) and then it works fine.
I'll research this a little more.

---

### Post by cyberdork33 on 2009-04-28
related bug:
[https://bugs.edge.launchpad.net/mactel-support/+bug/262408](https://bugs.edge.launchpad.net/mactel-support/+bug/262408)

---

