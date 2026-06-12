---
title: "system variables?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-03-28
1. In windows, at a command prompt you can type "set" and get the current system variables.  Is there something similiar in Linux? How about setting them?

---

### Post by IYY on 2006-03-28
I'm not 100% certain what you mean, but if you mean enviornment variables, then the command is: **env**

This will give you a list of all such variables, and their current values. To set one, use **read NAMEOFVAR** and type the value, or just NAMEOFVAR=somevalue.

---

### Post by oakz on 2006-03-28
To print out your current environment variables:

$ env

Environment variables can be set in your local bash session as mentioned above, or recorded in files to always get set...either in /etc/profile (for the whole system) or ~/.bashrc (for your user). An example in ~/.bashrc would be

export MY_ENV_PATH=/some/path

---

### Post by mlind on 2006-03-28
you can also specify temporary environment variable(s) for process you're launching at command line by
```

DISPLAY=:0.1 gmplayer &

```

will open mplayer gui on second display, and sends the process running on background.

---

