---
title: "How do I scroll up in a command prompt? [Resolved]"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Sammi on 2007-03-04
Sometimes one has to go to a real command prompt by pressing Ctrl-Alt-F6 or some other F-key. But I haven't been able to figure out how I scroll up to read text that has gone by. Page up doesn't work and ofcourse there is no scroll bar to the right like in gnome-terminal. Can anybody tell me how I can scroll up?

---

### Post by Aliarse on 2007-03-04
shift + page up/down

---

### Post by Sammi on 2007-03-04
Fantastic. Thanks Aliarse! :D

I tried to Google this, but I didn't find anything. Good thing one has the ubuntuforums to go to with noobish questions. Go ubuntuforums! :D

---

### Post by johnl on 2007-03-05
If you're expecting that a command will print a lot of output, you can also pipe it into 'less' (or 'more') which are programs that buffer the output and let you scroll up and down as well as search and many more features.

example:
```

$ cat /home/me/some_really_long_file | less

```

You can type 'man less' for information on specific key bindings to use once less is running.  For basic usage, all you need to know is page up, page down, and 'Q' to quit.

---

