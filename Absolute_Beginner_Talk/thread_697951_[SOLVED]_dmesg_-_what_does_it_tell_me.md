---
title: "[SOLVED] dmesg - what does it tell me?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by brett611 on 2008-02-15
Hello all,
It was suggested to me to check out the results of dmesg when I encountered a system lock up.  I've done that but frankly it might as well be sanscrit to me.  Any pointers for finding out how to decipher it would be appreciated!

Thanks

---

### Post by y-lee on 2008-02-15
I've been using that command when i help ppl tho I never looked for any explanations just been winging it :)

Anyway, found this article in Linux Gazette, [dmesg explained]("http://linuxgazette.net/issue59/nazario.html"). maybe that will help some, and btw I need to read thru it myself. lol

---

### Post by mbsullivan on 2008-02-15
Hi all,

Another place to look for system information is /var/log/syslog:

```
tail -f /var/log/syslog
```

You shouldn't really need to know 100% what every line in either means, but they can be useful for pinpointing problems for specific applications, daemons or drivers.

Mike

---

