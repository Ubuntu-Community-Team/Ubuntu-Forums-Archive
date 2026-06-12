---
title: "installing plugins in xmms"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by NitrOuS on 2006-01-10
I am trying to install aacplugin 1.1.4 in my xmms. And I have the following problem. When I type ./configure as the readme of the plugin says that xmms-config files misses and I can't continue the process. I searched the web and I found out that xmms-config is part of xmms-devel package in redhat, it's a rpm package. I downloaded this rpm and I tried to convert to deb with alien but this wasn't possible...There are problems & limitations using alien...What can I do to install this plugin?

---

### Post by nihilocrat on 2006-01-10
I don't think you need to compile the plugin yourself. Just get the "xmms-mp4" package, which describes itself as "a mp4/aac audio player for xmms".

Otherwise, if that's not the case....

Just get the xmms-dev package. No need to fool around with rpms. If you need to search for Ubuntu packages in the future, type this in a shell (without the *, of course) :
```

apt-cache search *name of what you're looking for*

```

---

