---
title: "How do you increase Tcp Max Connect Retransmissions in ubuntu?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by chaoswings on 2007-10-05
How do you do it? I know how to modify it for windoze....but I'm lost for linux

---

### Post by powder on 2007-10-05
You will find all of the IP related settings in this directory...

```
/proc/sys/net/ipv4
```

You can type ```
man tcp
``` in the terminal to see a description of each file or you can go to this link to view the same information.

[http://node1.yo-linux.com/cgi-bin/man2html?cgi_command=tcp](http://node1.yo-linux.com/cgi-bin/man2html?cgi_command=tcp)

---

