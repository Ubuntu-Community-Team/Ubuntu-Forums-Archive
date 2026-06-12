---
title: "Compiz Fusion Starts Manually Only"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-07-01
If I load Compiz Fusion in a terminal or Alt+F2 with 
```
compiz --replace -c emerald &
```
it works fine.

But if I use the same code in a start-up item for a session, or even as a script, it doesn't work.

What gives? 

I have tried the compiz.wrapper as an alternative, because I use emerald, but I couldn't get it to function properly. 

Any help?

I( realize there are lots of threads about start-up issues with Fusion, but they have gotten so complicated, I wanted to start fresh. i have been through every thread I could find, and did not find a solution that worked for me. Using the Beryl Manager to select Compiz and Emerald does not work.

I have already set metacity as my default wm in gconf

Thanks.

---

### Post by coldstatue on 2007-07-01
the solution for me was to give the full path to the script in sessions manager, even though I had it selected in rcconf.

I turned it off in rcconf, and now it works.

---

