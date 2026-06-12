---
title: "Error &quot;File not found&quot; while deleting"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Jeremy88 on 2007-04-24
I get this error when trying to delete these files from the Trash Biin. Anyone know how to fix this?

[img]http://img472.imageshack.us/img472/7328/snapshot2uk2.png[/img]

---

### Post by imspecial on 2007-04-24
were those files originally created, saved, or edited under the root account?

if so just try navigate to your Trash Bin from the command line
```
cd ~/.Trash
```
and run this (only if you want to remove everything but I am assuming you do)
```
sudo rm -rfR *
```

---

