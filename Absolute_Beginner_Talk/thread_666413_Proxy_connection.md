---
title: "Proxy connection"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by karthikophobia on 2008-01-13
hi
Im using Gutsy and am connected to net through a proxy server.
Some of my applications like 'amarok' and 'dictionary' are not able to connect to the net.
plz help.

Thanq

PS: sry, I for got to mention that I'm using GNOME.

---

### Post by mattismyname on 2008-01-13
Karthik-  This is just a guess but perhaps there is a proxy setting inside the amarok configuration.  Try looking what options amarok will let you set.

For 'dictionary' I'm not sure...is that a command line tool or GUI?  A lot of times you can set the environment variable HTTP_PROXY for a lot of apps.  You may even want to try that with amarok.

For example, if you're using the default bash shell:

```
export HTTP_PROXY="http://yourproxy.com:8080"
amarok
```

---

