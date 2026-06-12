---
title: "How do I change a default icon?"
date: 2006-06-14
forum: Art &amp; Design
---

### Post by johnc4510 on 2006-06-14
There is one icon that just bugs me, the reload icon. I know where it's location is:
/usr/share/icons/Human/16x16/actions
And I know the one I want to use instead, and I know where it's location is:
/usr/share/iconsTango/22x22/actions
But I can't seem to get it changed. Any ideas?

---

### Post by weijie90 on 2006-06-14
why don't you rename the default reload icon to "<original name>Backup" and copy the tango icon to the location of the human icon and remame it to the human reload icon filename?

---

### Post by aysiu on 2006-06-15
```
sudo cp /usr/share/icons/Human/16x16/actions/reload.png /usr/share/icons/Human/16x16/actions/reload_backup.png
sudo cp /usr/share/icons/Tango/22x22/actions/reload.png /usr/share/icons/Human/16x16/actions/reload.png
```

---

