---
title: "Setting environment variables"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2006-10-29
Hi,

I tried setting an environment variable with: ```
export NAME=location
``` in Eterm, but setting this variable only seems to last for the length of the Eterm session -- so when I close it, it's gone.

How can I permanently set an environment variable?

Regards

---

### Post by Najand on 2006-10-29
Add the command to your ".bashrc" file in your home directory.

---

### Post by lloyd_b on 2006-10-29
> I tried setting an environment variable with:
Code:

```
export NAME=location
```

in Eterm, but setting this variable only seems to last for the length of the Eterm session -- so when I close it, it's gone.

How can I permanently set an environment variable?

It depends on what "shell" you are running inside of Eterm.  Most likely, you're running "bash", in which case just edit the file ".bashrc" in your home directory, and add that export line into it.

To find out what shell you're running (if you don't already know), type "ps" in a terminal window.  This will respond with two lines, one for the "ps" itself, and the other for the shell.

If you're running with a different shell, then the file you'll need to edit will be different.

Note: After editing ".bashrc", the environment variable will NOT show up in the current session.  You'll have to close that terminal window and open another one before the change takes effect.

Lloyd B.

---

