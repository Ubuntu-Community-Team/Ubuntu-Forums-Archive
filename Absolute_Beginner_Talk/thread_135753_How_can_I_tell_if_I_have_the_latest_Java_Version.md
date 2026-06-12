---
title: "How can I tell if I have the latest Java Version?"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-02-24
I've downloaded and installed what I think is the latest Java version, in accordance with the Wiki instructions.

All seemed to go OK, but I'm still getting messages in Firefox that I need to update my JVM version.

Before I go to tech support for the item I'm trying to view, is there a way of telling what Java version I'm running?

---

### Post by jrib on 2006-02-24
```
java -version
```

```
sudo update-alternatives --config java
```
will let you choose between various versions

maybe ```
sudo update-alternatives --config firefox-javaplugin.so
``` for firefox...

---

### Post by mdsmedia on 2006-02-24
thanks Jason. I think that tells me all I need to know.

If I updated Java, I'm guessing I don't need to reboot for it to become effective in Firefox?

---

