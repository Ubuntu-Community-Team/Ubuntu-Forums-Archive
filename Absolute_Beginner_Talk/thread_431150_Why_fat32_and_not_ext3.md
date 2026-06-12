---
title: "Why fat32 and not ext3?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-02
Uhm, I'm just curious about something and please do correct me if I'm wrong. Why do so many choose to use a Fat32 partition instead of an ext3 partition, when it comes to sharing data with Windows XP?

Why do so when Fat32 has various issues like permission problems which make your life way more difficult?

---

### Post by bobplano on 2007-05-02
well fat32 is readble by both OSes so you don't need ntfs3g or efs(whatever it is). so there may be issues with it but almost any OS can read it making it a great file storage filesystem

---

### Post by 23meg on 2007-05-02
Perhaps because Windows can't read or write to EXT3 natively, and they don't know about or don't trust EXT2IFS.

---

### Post by az on 2007-05-02
> **23meg said:**
> Perhaps because Windows can't read or write to EXT3 natively, and they don't know about or don't trust EXT2IFS.

In windows, install the ext2/ext3 driver from fs-driver.org.

It allows windows to use ext3 partitions as native windows partitions, except it does not recognize permissions (well it does, but it mounts it as root).

I don't run windows, so I don't care about the security implications of windows being able to write to your linux partition, but  it is a stable driver and it works.

---

### Post by Drooling Iguana on 2007-05-02
Because I'd prefer to avoid giving Windows any type of access to my Linux partition. I just feel better knowing that Linux can read my Windows drives but not the other way around.

---

