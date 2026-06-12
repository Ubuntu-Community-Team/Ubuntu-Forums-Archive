---
title: "Icons for mounted partitions on desktop"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by michael_besselman on 2007-05-20
I have mounted my two windows partitions from Ubuntu, but there are now two icons on the desktop from them.  How can I remove the icons and still have the drives mounted?

Thanks

---

### Post by Kobalt on 2007-05-20
Press Alt+F2, enter *gconf-editor*, navigate from apps > nautilus > desktop. Uncheck volumes_visible.
you're done :)

---

