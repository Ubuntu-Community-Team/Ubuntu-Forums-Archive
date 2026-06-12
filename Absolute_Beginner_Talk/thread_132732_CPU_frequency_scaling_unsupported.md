---
title: "CPU frequency scaling unsupported"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by SMF on 2006-02-18
When I launch ubuntu I get this:

[IMG]http://img70.imageshack.us/img70/4547/unsupo4zq.jpg[/IMG]

Why is this poping up and how can I fix it?

Thank you.

---

### Post by moephan on 2006-02-18
My guess, and this is just a guess, is that your CPU does not support CPU Frequency scaling but the powernowd daemon was installed and tried to run at startup, realizes that the CPU doesn't support it and throws an error. If this is the case, then removing powernowd should fix the problem. Powerowd tries to run your CPU slower when it isn't being used much to save power.

You might want to check in the System Log Viewer to see if powernowd left any messages for you there.

Cheers, Rick

---

### Post by tnilsson on 2006-02-21
After the last kernel update i Breezy the CPU frequenzy scaling stoped working.
Any ideas on what to do?

This is regarding kernel:
2.6.12-10-686 #1 Mon Feb 13 12:18:37 UTC 2006 i686 GNU/Linux

---

