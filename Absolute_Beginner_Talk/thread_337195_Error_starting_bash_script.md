---
title: "Error starting bash script"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by PaperPilot on 2007-01-12
Hi All:

I am running Ubuntu 6.06 and Have a bash script starting:

#!/bin/sh

The error message:

sh: /etc/ppp/ppp-on-dialer: /bin/sh^M: bad interpreter: No such file or directory
Connect script failed


What did I do wrong?

Thanks in advance.

---

### Post by bscbrit on 2007-01-12
Change the first line to read

#!/bin/bash

The problem is that the alias for 'sh' is not set for 'bash'.

---

### Post by po0f on 2007-01-12
PaperPilot,

[Link](http://www.ubuntuforums.org/showthread.php?p=2003905#post2003905).

The problem is that you downloaded this script onto a Windows box and transferred it to your Linux box.

---

### Post by bscbrit on 2007-01-12
po0f - good point!

---

### Post by PaperPilot on 2007-01-14
> **po0f said:**
> PaperPilot,

[Link](http://www.ubuntuforums.org/showthread.php?p=2003905#post2003905).

The problem is that you downloaded this script onto a Windows box and transferred it to your Linux box.
Although I found it on a windows box (my Ubuntu box isn't connected to the web), I took it from a Linux web page.

---

### Post by PaperPilot on 2007-01-14
> **bscbrit said:**
> Change the first line to read

#!/bin/bash

The problem is that the alias for 'sh' is not set for 'bash'.
I changed the command as suggested amd got the same error.

---

### Post by PaperPilot on 2007-01-14
You were right; it was a character set problem.

Now I can't get the script to write to a file.  Oh the problems.

---

### Post by po0f on 2007-01-14
PaperPilot,

[quote=PaperPilot]... I took it from a Linux web page.[/quote]

Irrelevant.  The fact remains that you downloaded the script onto a Windows box.  All the newline characters were translated from '\n' to Windows' '\r\n', this is why you're getting that extra character ^M in "/bin/bash^M".

As for the script not writing to a file, you could use `sudo bash script.sh` to run it.  I'd look into what it was trying to write to first beforehand to make sure you want it to do what you're asking it to do.

---

