---
title: "uninstall / remove software -- Dominions 3 awakening"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by ImAnOgre on 2008-03-06
Hello all.  I installed a game (dominions 3 awakening) from the CD using a .run file.

Is there a easy way to uninstall this game from the terminal?

Can I just delete the file created when I made the directory and be done with it?

TIA.

---

### Post by jfinkels on 2008-03-06
> **ImAnOgre said:**
> Hello all.  I installed a game (dominions 3 awakening) from the CD using a .run file.

Is there a easy way to uninstall this game from the terminal?

Can I just delete the file created when I made the directory and be done with it?

TIA.

Was there any documentation that came with your ".run file"? A README or something? Can you post the contents of the script, so that we can get any idea of what it installed?

I don't really understand what you mean in your second question, but if you are certain that the script only created one directory and all game files are in that directory, then sure, delete it. That's what an uninstall script would do anyway.

---

### Post by PeterJS on 2008-03-06
As jfinkels said with out seeing the script we can't know what it did in order to undo it. If it's a wholly self contained subdirectory of /opt/ (but only if then, and this is rarely the case, you'll likely have some symlinks to hunt down at the very least) you can just delete the folder and be done with it.

And this is why package management systems are good. Though traditionally used when compiling from source, you can also use checkinstall to build deb packages from any script. So in the future if you have to install something funny from a .run file or other non-standard installer you can use:
```

sudo checkinstall ./scriptname

```

---

