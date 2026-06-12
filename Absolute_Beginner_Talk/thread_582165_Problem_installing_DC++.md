---
title: "Problem installing DC++"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Bleakesth on 2007-10-19
Hi there,
apologies if this is in the wrong forum, but here goes. I'm trying to install dc++ on ubuntu, ive done everything exactly as the various tutorials floating around says to, but when it gets to the part where I have to compile it I get this message:

scons: *** Error writing options to file: build/sconf/scache.conf
[Errno 2] No such file or directory: 'build/sconf/scache.conf'

Anyone know where i'm going wrong? Any help would be much appreciated!

---

### Post by K.Mandla on 2007-10-26
Moved to Absolute Beginner Talk.

---

### Post by janne_oksanen on 2007-10-26
I'm also having problems compiling linuxdcpp. What I'm getting is:

```
janne@Dominator:~/linuxdcpp$ sudo scons
scons: Reading SConscript files ...
IOError: [Errno 2] No such file or directory: './build/sconf/.sconsign.dblite':
  File "SConstruct", line 67:
    env.SConsignFile('build/sconf/.sconsign')
  File "/usr/lib/python2.4/site-packages/SCons/Environment.py", line 1151:
    SCons.SConsign.File(name, dbm_module)
  File "/usr/lib/python2.4/site-packages/SCons/SConsign.py", line 220:
    database = dbm_module.open(name, "c")
  File "/usr/lib/python2.4/site-packages/SCons/dblite.py", line 109:
    return dblite(file, flag, mode)
  File "/usr/lib/python2.4/site-packages/SCons/dblite.py", line 49:
    _open(self._file_name, "wb", self._mode)

```

Any ideas?

---

### Post by gszyszka on 2007-10-28
> **Bleakesth said:**
> Hi there,
apologies if this is in the wrong forum, but here goes. I'm trying to install dc++ on ubuntu, ive done everything exactly as the various tutorials floating around says to, but when it gets to the part where I have to compile it I get this message:

scons: *** Error writing options to file: build/sconf/scache.conf
[Errno 2] No such file or directory: 'build/sconf/scache.conf'

Anyone know where i'm going wrong? Any help would be much appreciated!

$ cd linuxdcppdirectory
$ mkdir -p build/sconf
$ scons

Should help

---

