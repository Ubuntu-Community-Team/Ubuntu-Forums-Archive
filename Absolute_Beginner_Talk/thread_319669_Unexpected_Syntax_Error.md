---
title: "Unexpected Syntax Error?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by okt on 2006-12-16
I am trying to install some drivers for my NIC and well, not having very much fun in the process.

I extracted the "DriverInstall" dir to my Desktop, and went to run the ./install.sh

I get an output of:
./install.sh: 71: Syntax error: "(" unexpected


Now if I am missing a dependency or something, how can I get it if I can't access the internet to grab them from a rep?

---

### Post by faraazs on 2006-12-16
What does line 71 have on it?

---

### Post by okt on 2006-12-16
> **faraazs said:**
> What does line 71 have on it?

It is the first line of code, everything before is commented out.
```
Function message_status ()
```

---

### Post by jpkotta on 2006-12-16
I'll bet there is a line at the top of the script that says "#!/bin/sh", and I'll bet if you change it to "#!/bin/bash" it will work.

---

### Post by okt on 2006-12-16
> **jpkotta said:**
> I'll bet there is a line at the top of the script that says "#!/bin/sh", and I'll bet if you change it to "#!/bin/bash" it will work.


Yea I did that just before refreshing the page, now it ran, but still no internet.

---

