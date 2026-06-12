---
title: "synaptic &quot;starting without administrative privileges&quot;"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by kallywag on 2008-01-10
I just reinstalled Ubuntu Gutsy because every time I try to customize something I end up breaking something and not being able to fix it.  Before, when I opened Synaptic Package Manager, it would prompt me for my password before I could add new software.

Since I've reinstalled, when I try to open Synaptic it gives me the 'starting without administrative privileges' message and then I can't install anything.

I can run sudo synaptic and it works fine, but how can I get it to just prompt me for my password like it used to? I don't like having to open terminal just to open synaptic. Any ideas?

---

### Post by mikewhatever on 2008-01-10
Assuming you are talking about the menu entry System>Admin>Synaptic, try checking the command invoked by it. Open System>Preferences>Main menu, find Synaptic, right click and select Properties, make sure the command starts with gksudo and if not add it.

---

### Post by kallywag on 2008-01-10
thank you - you are a genius. i checked and the shortcut was 'gksu' instead of 'gksudo' -- changed it and it worked. no idea how that could have gotten messed up though. thanks again!

---

