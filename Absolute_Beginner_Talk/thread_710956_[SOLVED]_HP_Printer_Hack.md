---
title: "[SOLVED] HP Printer Hack"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Amivit on 2008-02-29
I'm guessing that this is the right place to post according to this:

> The perfect starting place to find out more about computers,** Linux** and Ubuntu.

I need help compiling this script,
[http://www.irongeek.com/downloads/hpunix.c]("http://www.irongeek.com/downloads/hpunix.c")
But I have no idea what to search to find out how, so hoping someone will kindly help me out :) .
Thanks a lot!

By the way, here is some background information about the script:
[http://www.irongeek.com/i.php?page=security/hphack]("http://www.irongeek.com/i.php?page=security/hphack")

I found out, never mind !
EDIT The website tells me how lol :b

---

### Post by igknighted on 2008-02-29
If you are running Ubuntu, type this command to install the proper compilers:
```
sudo apt-get install build-essential
```

Then, once installed, download the script to your desktop.  Open a terminal and type 'cd Desktop' (D must be capital).

Use this command to compile it:
```
gcc hpunix.c
```

Then use this command to run it:
```
./a.out
```

---

