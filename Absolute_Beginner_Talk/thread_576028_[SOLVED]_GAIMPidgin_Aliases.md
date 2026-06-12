---
title: "[SOLVED] GAIM/Pidgin Aliases"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Gwasanaethau on 2007-10-14
I wonder if anyone can help me. I use GAIM/Pidgin (whatever you want to call it now) to connect to MSN. When people (buddies) log in, their aliases used to change to whatever they had assigned them to themselves, and they used to remain between sessions. Now, as soon as I log out, the alias is removed and their old name appears next time I log in. Does anyone know what's causing this, and, if possible, how to allow aliases to persist between sessions?

Thanks a mill!

---

### Post by defrex on 2007-10-14
I don't know about your problem specifically, but I can tell you that deleting the folder ~/.purple will reset all of Pidgin's settings. Perhaps give it a try. It'll mean reconfiguring everything, but it might be worth it.

---

### Post by Gwasanaethau on 2007-10-14
> **defrex said:**
> I don't know about your problem specifically, but I can tell you that deleting the folder ~/.purple will reset all of Pidgin's settings. Perhaps give it a try. It'll mean reconfiguring everything, but it might be worth it.
Thanks, but I've already given that a go. Good idea, though!

---

### Post by Gwasanaethau on 2007-10-14
I think I've found an answer: it looks like it's a bug in Pidgin itself:
[http://developer.pidgin.im/ticket/2571]("http://developer.pidgin.im/ticket/2571")
(By the way, when I mentioned 'aliases' in the previous comments, I actually meant 'nicknames'… ;) )

---

