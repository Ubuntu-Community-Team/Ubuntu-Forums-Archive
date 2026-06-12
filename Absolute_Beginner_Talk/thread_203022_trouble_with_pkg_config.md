---
title: "trouble with pkg_config"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by holiday on 2006-06-24
I understand that I should be using apt for all installations, but I really want the latest kino so I'm compiling it myself. I've built applications before so I'm familiar with the basic process.

When running configure on kino I get this:

```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBDV... configure: error: Package requirements (libdv >= 0.103) were not met:

Package libdv was not found in the pkg-config search path.
Perhaps you should add the directory containing `libdv.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libdv' found
```

But libdv is installed, and  > 0.103

```
# apt-get install libdv4
Reading package lists... Done
Building dependency tree... Done
libdv4 is already the newest version.
```

and there is no libdv.pc

```
# slocate libdv.pc
#

```
What's going on?

---

### Post by rai4shu2 on 2006-06-24
When compiling, you need to make sure you have the "-dev" files, which are the headers that the source files are expecting to find.

So, in your case, you should make sure you have the "libdv4-dev" package installed.

---

