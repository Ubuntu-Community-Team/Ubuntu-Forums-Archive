---
title: "bitchx shortcut and scripting"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Tashu on 2008-03-25
I'm wondering how can I script the same server, registering my nickname and join a channel as a shortcut on my desktop?

I tried to google around but I'm not sure what are the right terms for those in linux.

---

### Post by hellonull on 2008-04-29
Right click on the desktop and create a launcher. Set type to "Application in terminal."

For command, use the following format:
```
bitchx -c \#channel nick server
```

For more information on command line options for bitchx, type "info bitchx" in terminal.

**EDIT 4/30/08** Added the backslash before the # in the code. The # needs to be escaped as it is a reserved character in the command line.

---

