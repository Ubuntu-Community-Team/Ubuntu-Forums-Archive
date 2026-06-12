---
title: "AVG error"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-18
i recently got AVG, i dont know why, i think its the fact i can.

i went for a scan and only scan /bin/
which was 108 files, it said permission denied.

i run ```
avgscan /
``` as root in CLI
and still no luck

---

### Post by skymera on 2007-06-18
anyone?

---

### Post by orb9220 on 2007-06-18
Since it is a system root did you try **sudo avgscan /**?

But why are you running it for linux?
and a virus would not end up on your root partition unless you allowed it. If a program tries to install it would ask you for a password before it was allowed to be installed.


The only real reason to run it would be if you were running a server for email,ftp etc... and wanted to scan emails going to windows machines.

---

### Post by skymera on 2007-06-18
i got it to protect my computer from myself...
i install any crap

---

