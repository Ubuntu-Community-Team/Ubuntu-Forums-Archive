---
title: "Connect internet"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by luckymancvp on 2008-03-31
How could I change connect internet by proxy: 127.0.0.1 and port 8080.
(firefox and Pidgin or all).

---

### Post by dannyboy79 on 2008-03-31
you aren't being very specific so I have to make some assumptions. Within Firefox Web Browser, go into Tools, Options, then under the Advanced Section, then under the Network Tab, hit the Settings button under the Connection Area. There you can set your proxy server and port.

---

### Post by dstew on 2008-03-31
To let all your applications use the proxy server, I think you need to set an environmental variable:```
export http_proxy="http://127.0.0.1:8080/"
```

---

