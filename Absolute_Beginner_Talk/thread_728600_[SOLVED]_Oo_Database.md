---
title: "[SOLVED] Oo Database"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Andre_3608 on 2008-03-19
Please help.  On attempting to open a Table, the following error message appears:  OpenOffice.org requires a Java runtime environment (JRE) to perform this task.  The selected JRE is defective.  Please select another version or install and select it under Tools - Options - OpenOffice.org - Java.

I do not know how to do this.

The defective JRE is 1.5.0_13/jre

---

### Post by Xiong Chiamiov on 2008-03-19
When you go to tools->options->openoffice.org->java, does 1.5 appear in the list, and is it selected?
When you search for java in Synaptic, can you give us the exact name that appears for the package (eg. java-6-sun)?

---

### Post by Xiong Chiamiov on 2008-03-19
from pm: > **Andre_3608 said:**
> Many thanks for the help - I seem to be blundering from one obstacle to another (prime example of a little knowledge being dangerous). Synaptic allows me to install Sun-java6-jre; but comes with the rider "NOTE: You must accept Sun's EULA prior to successfully installing this package". I do not have a clue how to accept Sun's EULA.

Ah, my roommate had that problem.  If I remember right, we tried doing this in the terminal
```

sudo apt-get install sun-java6-jre

```
and that worked.  I'm not sure exactly what it was that we did to make it work, but have no fear! it *is* possible.

---

