---
title: "selecting files recursively for removal"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by TVu on 2006-08-10
It seems I can't figure out the correct command line syntax for this:

I have a directory with several multi-leveled subdirectories. Among thousands of files i want to keep there, there are also hundreds or so files i want to remove from all sublevels. All files to be removed are named alike.
I can find them all right, with ```
find /home -name "filename"
``` but how to pass the result to rm-command? Simple pipe like ```
rm | find...
``` won't do it.

regards, 
Tero

Edit: Found solution. This command did what I wanted:
```
find ./ -name "filename" -exec rm {} \;
```

---

### Post by MrHorus on 2006-08-10
> **TVu said:**
> 
I can find them all right, with ```
find /home -name "filename"
``` but how to pass the result to rm-command? Simple pipe like ```
rm | find...
``` won't do it.


A regular expression should do it.

[code]rm -rf <regex> <dir root>[code]

---

### Post by TVu on 2006-08-10
> **MrHorus said:**
> A regular expression should do it.
 Ok, now i feel dumb. Don't know what I was thinking there. Thanks for your help!

---

