---
title: "Swiftfox?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2006-06-03
How can I make swiftfox recognise my Java installation's and flash? Firefox does, but not Swiftfox.

---

### Post by angkor on 2006-06-03
I think you need to create a symlink in your swiftfox plugin directory to your libjavaplugin_oji.so.

Do a search for that file and create the symlink in your plugin dir.

```
ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so
```

Something like this, but you need to modify the paths according to your situation.

---

### Post by xael on 2006-06-03
You can also open two file browser windows (one with the contents of FF's plugin folder & the other with the contents of Swift's plugin folder & then link the plugins from FF to Swift). It's probably kind of lazy but it works.

---

