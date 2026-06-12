---
title: "Custom kernel causes flash problems?"
date: 2008-03-05
forum: Apple Intel Users
---

### Post by Rog-Mahal on 2008-03-05
Currently I'm running a 2.6.24-rc8 kernel and I've been having problems with getting flash to run. I tried the script [here]("http://ubuntuforums.org/showthread.php?t=476924") and it seemed to install correctly, but when I try to load the driver, I get the following error:

```
roger@hephaestos:~$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: 1: Syntax error: word unexpected (expecting ")")
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
```

I've already posted about this in the x86_64 forum and Kilz told me this might be an issue with custom kernels. I figured I'd bring the issue into this forum also. 

So, anyone with a custom kernel have similar errors/fixes?

Thanks.

---

