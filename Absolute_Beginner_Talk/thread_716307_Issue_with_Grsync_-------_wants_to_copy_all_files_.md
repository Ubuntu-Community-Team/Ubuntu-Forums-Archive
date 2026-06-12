---
title: "Issue with Grsync ------- wants to copy all files every time"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by HautingLu on 2008-03-05
I'm not sure if my settings are wrong, but it seems like it wants to sync (transfer) all my files every time. I'm doing a simple HD ----> portable HD sync. 

Settings were set at:
[LIST]
[*]Delete on destination
[*]Verbose
[*]Show transfer progress
[/LIST]

Everything else is unchecked. If I do an Execute, let it run through, then do Simulation again the same files show up.

Now if I check **Size Only** it seems to behave better, listing only the new files. I would like it to do checksums checks not to recopy all the files every time.

Thanks.

---

### Post by jcwmoore on 2008-03-05
my guess is, it's the verbose, that spits out everything, so my guess is you are seeing the output from every the file check.

---

