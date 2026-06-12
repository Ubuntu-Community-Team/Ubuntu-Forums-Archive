---
title: "Error: Extra junk at end of file?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-14
Trying to make linux go through a proxy server for installs etc, was told to write

Acquire::http::Proxy "http://insert.yourproxyurl.here"

in /etc/apt/apt.conf

Now when i try to doa nything i get

E: Syntax error /etc/apt/apt.conf:2: Extra junk at end of file

Me stuck... ?? Any ideas?

---

### Post by Ragazzo on 2007-01-19
There must be a semicolon ; at the end of each line

```

Acquire::http::Proxy "http://insert.yourproxyurl.here";

```

---

### Post by maccawolf on 2007-03-18
I'm getting the same error and I haven't ADDED any programs. Only performed the obligatory update. Can I undo it? there were 139 updates, how do I figure out what was updated?

---

