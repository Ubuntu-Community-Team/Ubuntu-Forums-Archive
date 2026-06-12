---
title: "packages"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by montablac on 2006-03-09
ok,im seting up the schools ibooks to linux,but were behind a proxy sever that requires authenciacation (sp?) and it wont let me through unless i supply a user name and password (yes i have one,and it does work,i just cant get it to prompt for it)

but it NEEDS to be in synaptic other wise the school admin will have no idea how to get the latest programs and stuff

but ANY help with this would be great

and if any one also knows how to make a script to set the time when the computer starts up,that would be great to
(the time bug strikes again)

--montablac

---

### Post by rboss on 2006-03-10
You can tell apt-get (and thus synaptics) use a proxy by adding the following lines to /etc/apt/apt.conf:
```

Acquire::http::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/";
Acquire::ftp::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/"

```

---

