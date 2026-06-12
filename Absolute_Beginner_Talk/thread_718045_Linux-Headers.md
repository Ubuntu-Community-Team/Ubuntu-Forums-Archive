---
title: "Linux-Headers"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Tywin on 2008-03-07
Hi there,
i need for an application (vmware) installed linux-headers for my ubuntu 7.04
uname -a says

Linux <xxcutxx> 2.6.24.2-xxxx-std-ipv4-32 #1 SMP Mon Feb 11 15:26:43 CET 2008 i686 GNU/Linux

when i do

sudo apt-get install linux-headers-2.6.24.2-xxxx-std-ipv4-32

it doesnt find any ... with aptitude i also find only .16 .19 and .20 linux-header files

how can i solve this? is there even a solution?

greets

---

### Post by Crooksey on 2008-03-07
```

$ sudo apt-cache search linux-headers
```

I think the command to install kernel headers is something like...

```

$ sudo apt-get install linux-headers-($uname-r)
```

---

### Post by jimv on 2008-03-07
That's odd...did you install a newer kernel?  7.04 should have 2.6.20.16 or something like that.  2.6.24 is much newer, and the kernel headers won't be in the 7.04 repos.

---

