---
title: "Does failed driver installation effect system?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by ljpm on 2007-01-15
Hi all,

I have tried to install ati video drivers 3 or 4 times now with no success. I have been able to recover by replacing the modified xorg.conf with a back up I created. I was just wondering if these failed attempts have messed up anything else in my system (Ubuntu Dapper, fresh install). I realize I can simply install again, but that is really getting tiring (have installed half a dozen times already). 

For other newbies, before you try to install video drivers back up your xorg.conf

```
cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Then if things go drastically wrong and you are left no GUI you can enter the following at the text prompt.

```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```




Also, in general, is there any easy way to undo a failed installation of any thing? (I still am having more failures than successes with installing things in UBUNTU)

---

### Post by xpod on 2007-01-15
Sorry to hear your woes ljpm but i like your persistance.
I too re-installed many times during my inital attempts with the Nvidia drivers and beryl etc but if nothing else at least you have become quite expereinced at the install procedure:D .......which is the most important after all(imho)

Mabey if you let these folks know which guides and methods & drivers you`ve tried then things might be a bit easier to fathom out........not by me of course but someone will:mrgreen:

---

