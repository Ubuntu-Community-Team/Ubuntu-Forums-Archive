---
title: "wine problem"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-10-05
i am trying to run a program with wine, it was working fine last night and earlier today, but now i get this error in my terminal window over and over again for a very long while. the program wont start and i cant get wine to start either.

```
err:syslevel:_CheckNotSysLevel Holding lock 0x7eaa0aa0 level 3
err:syslevel:_EnterSysLevel (0x7ebad840, level 2): Holding 0x7eaa0aa0, level 3. Expect deadlock!

```

---

### Post by TeaSwigger on 2007-10-05
Hello, I have absolutely no clue what any of that means. But anyway ;) a question: do all WINE apps fail that way or only one? If only one, you could try to uninstall it, reinstall it, try another windows version to emulate (in winecfg, see below if you're unfamiliar with that), etc. If it's WINE itself a couple of things to try I suppose, won't do any harm at this point...

In a terminal, type:

```
wineprefixcreate
```

and see if that takes. It should be busy for a min. If successfully back at the prompt type:

```
winecfg
```

Should bring up the WINE configuration window. See if everything seems right in there. If that's all good, could try uninstalling WINE and reinstalling, or trying an earlier version for now I suppose... 

Are there any things which were plugged in but are not now, like a camera, usb stick, anything? Any hardware changed?

Just trying to stir ideas.

---

