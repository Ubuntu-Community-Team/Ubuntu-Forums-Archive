---
title: "Fixing java in firefox"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by rj686 on 2005-09-16
Hopefully this is just for breezy but all along i've had the j2rel.5-sun package but the plugin never registerd. The guide doesn't give u the right thing to do.

heres how u fix it:

change to ur mozilla plugins folder(in my case):
cd /usr/lib/mozilla-firefox/plugins/

make a system link from your java folder to your plugins folder:
ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

and boom your done.

This may have just been for me but that package doesn't auto extract the plugin, you need to do it yourself.

---

### Post by flibble on 2005-09-21
Thank  you  very  much  indeed   :-P

---

