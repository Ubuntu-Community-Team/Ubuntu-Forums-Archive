---
title: "Is there a command that can be run from command line"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-05-31
to completely remove an app and it's dependencies??
Went to install wmware server and it won't install cause it sees vmplayer installed i never installed. so i went thru synaptic and removed it. It still complains that it's installed yet.. this is ubuntu/dapper

---

### Post by bruce89 on 2006-05-31
```
sudo aptitude remove <app>
``` But I think that it requires the packages to be installed with aptitude in the first place.

---

### Post by aysiu on 2006-05-31
[QUOTE=bruce89]But I think that it requires the packages to be installed with aptitude in the first place.[/QUOTE] Yes it does.

Unfortunately, if you used apt-get, Synaptic, or Adept, you're going to be stuck using *deborphan* or *gtkorphan* to try to get out all those "orphaned" dependencies.

---

### Post by bruce89 on 2006-05-31
Of course, Edgy will use smart package manager, so this package dependancy removal thing will work everywhere, I think.

[QUOTE=aysiu]Unfortunately, if you used apt-get, Synaptic, or Adept, you're going to be stuck using *deborphan* or *gtkorphan* to try to get out all those "orphaned" dependencies.[/QUOTE]
I always used to use deborphan, but thanks to you, I now have *gtkorphan* installed.  Actually I always use *aptitude* anyway.

---

