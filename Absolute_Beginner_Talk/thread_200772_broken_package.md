---
title: "broken package?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2006-06-20
Tried to do a system update and it said I got a broken package (how embarassing!) and said this:

E: /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.0ubuntu1_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0

Any clue as to what went wrong/how to fix this?  Is it worth worrying about?

---

### Post by user1397 on 2006-06-20
try pasting this in a terminal (applications, accessories, terminal): ```
sudo apt-get clean
``` and then ```
sudo aptitude update
```

---

### Post by xboxbman on 2006-06-21
[QUOTE=erik1397]try pasting this in a terminal (applications, accessories, terminal): ```
sudo apt-get clean
``` and then ```
sudo aptitude update
```[/QUOTE]
thank you. worked flawlessly

---

### Post by xboxbman on 2006-06-21
looks like i was lieing.  It's still broken.

---

### Post by jenco on 2006-07-30
Having same problem not a big deal but i hate errors while doing updates :P
And my update notifier won't go away ><

```
(Reading database ... 118109 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1.8.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1.8.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/liblavplay-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1.8.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

