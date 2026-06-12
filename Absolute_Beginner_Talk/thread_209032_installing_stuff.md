---
title: "installing stuff"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by rum and monkey on 2006-07-04
I feel pretty stupid asking this, but how do I install stuff? I was trying to install cube 2 ([http://sauerbraten.org/docs/config.html](http://sauerbraten.org/docs/config.html)) and I have absolutely no idea what any of that means. I tried following a guide ([http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)) but that didn't work either. When I tried the ./configure command I got: **bash: ./configure: No such file or directory** and when I tried "make" I got: **make: *** No targets specified and no makefile found.  Stop.** I'm so confused :confused: :confused: :confused:

---

### Post by wolfmaniac on 2006-07-04
why r u compiling from the source?
see resporatries to check the precompiled packages.

---

### Post by wolfmaniac on 2006-07-04
check out this link
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by aysiu on 2006-07-04
The instructions on that link say: > For linux: gunzip, run chmod +x sauerbraten_unix and then ./sauerbraten_unix I think that's supposed to say *unzip*, not *gunzip*.

So it'd be something like ```
chmod +x sauerbraten_unix
sudo ./sauerbraten_unix
```

---

