---
title: "Why are my HDD's folders?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by jas992 on 2007-01-08
Hi,

How do I make my mounted internal HDD's appear in the 'Computer-Filebrowser' as actual drives instead of folders within Filesystem? I hope my question makes sense. Any information would be truly appreciated. :)

Thanks in advance,
jas992.

---

### Post by xyz on 2007-01-08
Hi,
Can you please post the output of this:
```
sudo fdisk -l
```
Just copy/paste it in a terminal...go Applications > Accessories > Terminal

---

### Post by mahy on 2007-01-08
> **jas992 said:**
> Hi,

How do I make my mounted internal HDD's appear in the 'Computer-Filebrowser' as actual drives instead of folders within Filesystem? I hope my question makes sense. Any information would be truly appreciated. :)

Thanks in advance,
jas992.

This is the Unix way of handling filesystems and devices; i'm afraid there's no room for change. However, newbie-friendly GUI file browsers usually also display devices, don't they?

---

### Post by MindRiot on 2007-01-08
Either:

A. Click Computer on the main toolbar

or

B. Click the small button in the side bar and select Places, then click Computer on the main toolbar.

---

### Post by hal10000 on 2007-01-08
In linux any device, and your harddrives too, appear always as directories. (This is not a bug, it's a feature).

I guess in the nautilus file browser your mounted (or unmounted) drives appear under "media" or "places", but if mounted, the partitions will be handled by the filesystem like directories.
(I don't use gnome, so I can't tell you the exact menu entries for nautilus, sorry)

---

