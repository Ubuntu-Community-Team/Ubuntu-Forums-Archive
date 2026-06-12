---
title: "website loading very slowly"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-02-13
Hello,

I have the problem that internet pages are loading very slowly in FireFox and also Konqueror. I am using Gutsy.

It can't be a problem with the connection, since I am using WIndows Computer on the same network with Firefox and pages are loading fast on that.

How can I figure out what the problem is?

Looking forward to u suggestions,
Ben

---

### Post by zerhacke on 2008-02-13
Add the following to the bottom of the /etc/modprobe.d/blacklist file

```
ipv6
```

Reboot.

This will stop the IPv6 module from loading and your pages should become much quicker to load.

---

### Post by kiwinsn on 2008-02-13
You could also typr about:config in the Firefox window.
Search for IPv6 and change whatever is showing.

---

### Post by ben22 on 2008-02-13
what do u mean by reboot?

I have restarted the computer.

Do u mean I should enter a certain command to the command line.

---

### Post by zerhacke on 2008-02-13
> **kiwinsn said:**
> You could also typr about:config in the Firefox window.
Search for IPv6 and change whatever is showing.
That would only make firefox work faster.  It would not affect Konqueror or any other network aware program.

---

### Post by gemmala on 2008-02-13
I'm told when I try this that I do not have the necessary permissions to save this file - how do I get round this?

---

### Post by Jayzon11 on 2008-02-13
Sudo nano /etc/modprobe.d/blacklist

might work

---

### Post by jan quark on 2008-02-13
see here

[http://ubuntuforums.org/showthread.php?t=696069](http://ubuntuforums.org/showthread.php?t=696069)

---

