---
title: "Kernel updating install"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-01
I got this excerp because I am unable to compile from source code.

> in /usr/src there should be a folder called linux-source-4.6.10 or something similar.... first copy and paste /usr/src/linux into a safe folder for later (backup the old file), then use 'sudo ln -s /usr/src/linux-source-xyz /usr/src/linux' where xyz is the folder that i was talking about before that contained the source code... the linux-source-4.6.10 or similar one. good luck yet again!

My problem is that the /usr/src folder had nothing in it when I started compiling. Now how do I get that bit correct? I'm using Hoary and have downloaded the new kernel-headers, but where did it go?

---

### Post by adwait on 2005-08-01
Download the linux source and put it there. To download the sources you can use
```
sudo apt-get install linux-source
```

Or you can download source from [www.kernel.org](www.kernel.org).

---

