---
title: "&quot;dpkg: serious warning&quot; when sudo aptitude install?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-12-12
Hi,
As explained in the title, I may be running this command line:
```
sudo aptitude install (or remove) kino
```
or any other progs, I get this near the end:
> dpkg: serious warning: files list file for package `defrag' missing, assuming package has no files currently installed.
105150 files and directories currently installed.)
Removing kino ...
Running prelink, please wait...
Of course, when I read "serious warning", I start worrying! Should I?
What does it mean and what can I do, if anything, about it?
Thx for reading.

---

### Post by deadgobby on 2006-12-12
Do you get the same when you install Kino in Synantic?
Gobby

---

### Post by xyz on 2006-12-12
I haven't tried that but I will as soon as I can. I unexpectedly have to leave home right now. I'll keep in touch. Thx.

---

### Post by xyz on 2006-12-13
> **deadgobby said:**
> Do you get the same when you install Kino in Synantic?
Gobby
Yes, same thing!!

---

### Post by Bachstelze on 2006-12-13
Seems the package 'defrag' is the problem. Try reinstalling or uninstalling it.

---

### Post by xyz on 2006-12-13
Thanks for your replies.
I had tried installing/removing...'defrag' but no change!
"HymnToLife", you made me think of looking in Synaptic (Search defrag) to see if some dependencies were missing.

Strangely ```
sudo aptitude install defrag
``` didn't install these 2 requirements:
**1. libnids1.20  **
[i]Libnids performs assembly of TCP segments into TCP streams, IP
defragmentation, and TCP port scan detection.[/i]

**2. libnids-dev**
[i]Libnids code watches all local network traffic, cooks received datagrams a
bit, and provides convenient information about them to the NIDS analyzing
modules.[/i]
Now the "serious warning" is gone. Thx for your time.

---

