---
title: "Question about Temporary Files"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-12
In Windows, when a program crashed, temporary file were created. This could then be deleted using the Disk Cleanup utility. Is there a similar way that I can clear temporary files in Ubuntu 7.10 Gusty Gibbon?

Thanks for your time.

---

### Post by jan quark on 2008-02-12
you can always use
```

sudo apt-get autoremove
```

to remove not needed packages

and have a look at this How to : How to remove junk files

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by mrsteveman1 on 2008-02-12
If you mean random temporary files the system creates for various reasons, they usually get put in /tmp

/tmp gets cleared on every boot in most distributions

---

