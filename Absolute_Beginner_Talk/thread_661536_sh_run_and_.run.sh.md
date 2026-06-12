---
title: "sh run and ./run.sh"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-01-08
Hi.
What is the difference between:
1) ./runMe.sh
and
2) sh runMe
?
And when to use each one?
Thanks.

---

### Post by rufius on 2008-01-08
A command like "./runMe.sh" indicates that that script has "#!/bin/sh" or some other execute string at the first line of the file.

The other "sh runMe" means it contains shell commands, but needs to be fed to the "sh" shell program.

You just need to know if there's a line like "#!/bin/bash" at the top of the file. If there is, just do "./file.sh" otherwise, do "sh file".

Hope that helps!

---

### Post by hyper_ch on 2008-01-08
further more

```

./

```
means the current directory... if you just enter a filename afterwards it means run file XXX in the current directory.

```

sh /path/to/file

```
With that you can point to a file anywhere on the system.

---

