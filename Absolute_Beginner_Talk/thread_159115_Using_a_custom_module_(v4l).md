---
title: "Using a custom module (v4l)"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Dogmeat on 2006-04-12
Hello, I need to change the v4l module source because I want to add support to my remote control. I'm new to this process, and I wonder what is the right way to install a module I changed? I already got a v4l snapshot, and the kernel source. Is it really necessary to create a custom kernel? If possible I'd rather just backup the current module and put the new one in it's place, if this is possible.

Another thing: when compiling the module I get this:

```
make -C /lib/modules/2.6.12-10-k7/build SUBDIRS=/home/dogmeat/src/v4l  modules
make: *** /lib/modules/2.6.12-10-k7/build: No such file or directory.  Stop.
make: ** [default] Erro 2
```

I assume I must create the 'build' symlink pointing to somewhere, but I can't find any documentation about this and I don't want to overwrite anything on the current kernel, so I post this asking how I should proceed next. Thanks in advance!

---

