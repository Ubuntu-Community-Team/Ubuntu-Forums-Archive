---
title: "All I want to do is ... [Resolved]"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by NullaPax on 2007-04-05
... drag a file from the desktop into a folder.
When I try to it says I don't have permission.
I have looked in the help files and they make about as much sense to a non geek as Egyptian hieroglyphs to a slug.

I am not so devastatingly paranoid as to need all this protection from myself, is there a way I can make Ubuntu more accessible to myself ( hell, I own the damn PC. If I want to run it fast and loose then that should be up to me ) or must I continue to fight against an unfriendly system ? 

Thanks for any help.

*I want Linux to succeed, I really do, but as it is Microsoft must be rolling on the floor laughing their B******s off when anyone suggests that Linux is competition.*

---

### Post by taurus on 2007-04-05
You cannot write outside your $HOME directory so if you want to do that, use

<Alt>F2
```
gksudo nautilus
```

> I want Linux to succeed, I really do, but as it is Microsoft must be rolling on the floor laughing their B******s off when anyone suggests that Linux is competition.
:roll:

---

### Post by theninthdimension on 2007-04-05
I've never personally tried changing file or folder permissions yet. However, it looks like a fairly straight-forward operation. Open up a terminal and type in _man chmod_ (I only underline to show the command). This will bring up the instruction on how to change permissions for these things. It may be a good idea to double check what the file or folder you want to change the permissions on does just in case.

Jeff.

---

### Post by NullaPax on 2007-04-05
Thanks Taurus, that did it.

Sorry for the depreciating comment but I have been praying for Linux to take off for years and yet it seems to be determined to remain clunky and unfriendly to the average PC user.

I would love for Linux to do to Micro$oft what AMD did to Intel.

Thanks again :)

---

### Post by aysiu on 2007-04-05
This issue has been resolved.

I've moved the further discussion to [The Linux Desktop Readiness Thread](http://ubuntuforums.org/showthread.php?p=2406464#post2406464).

---

