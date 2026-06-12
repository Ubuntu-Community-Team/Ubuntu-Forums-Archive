---
title: "[SOLVED] Cannot Connect to Google"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by H3retic on 2007-11-13
I've had this problem with all of my previous ubuntu installs.
Simply put, after 2 weeks of using ubuntu, firefox will no longer connect to google.ca, google.com, or gmail.
In terminal, "ping google.ca" doesn't work either.

It's not a big deal, I mean I can just use yahoo, but Gmail is pretty important.

I can't connect through proxyweb.net either.

Help!

---

### Post by shad0w_walker on 2007-11-13
Just as warning. Don't run any rm command. It's a spammer. Check out the top sticky on the newbie forum section.

---

### Post by bapoumba on 2007-11-13
Read my sig, please, last line.

---

### Post by philinux on 2007-11-13
open a terminal and type ```
firefox -safe-mode
```

See if you can connect

---

### Post by H3retic on 2007-11-13
Whats all this -rm stuff stand for?

firefox -safe-mode
=
Testing now

---

### Post by H3retic on 2007-11-13
Safe mode=no good

Disabled everithing and still not working.

---

### Post by H3retic on 2007-11-13
Solved!

I opened up Moblock GUI and guess what it showed:

Blocked OUT: Google Inc,hits: 3,DST: 64.233.161.104
Blocked OUT: Google Inc,hits: 4,DST: 64.233.161.104
Blocked OUT: Google Inc,hits: 5,DST: 64.233.161.104
Blocked OUT: Google Inc,hits: 1,DST: 209.85.135.91
Blocked OUT: Google Inc,hits: 2,DST: 209.85.135.91
Blocked OUT: Google Inc,hits: 3,DST: 209.85.135.91
Blocked OUT: Google Inc,hits: 4,DST: 209.85.135.91
Blocked OUT: Google Inc,hits: 5,DST: 209.85.135.91

I didn't know it was enabled from startup.  Well, at least I know it works!

---

