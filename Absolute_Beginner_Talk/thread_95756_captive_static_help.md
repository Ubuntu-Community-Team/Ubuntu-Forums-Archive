---
title: "captive static help"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by danne on 2005-11-27
hi,
I've just installed captive static for writing in ntfs...
now i'm trying to configure it but I'm stuck here's what i've done so far

```
# captive-cmdline \
--load-module=/var/lib/captive/ntoskrnl.exe \
--filesystem=/var/lib/captive/ntfs.sys \ --sandbox-server=/usr/sbin/captive-sandbox-server \ --bug-pathname=/tmp/captive-bug-%FT%T.captivebug.xml.gz \
--disk --rw /dev/hda1
```

on the [site]("http://www.jankratochvil.net/project/captive/"), they talk about LUFS but I don't know if i have to install that too??

any help for further config would be nice!

kind regards,

Danne

---

