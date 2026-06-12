---
title: "[SOLVED] Where is videolan-doc?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by t0p on 2007-12-25
I've installed the package **videolan-doc**, which is described in Synaptic like this:

> documentation for the VideoLAN streaming solution
This package contains useful documentation for the VideoLAN streaming
solution: the VLC Play HOWTO (a complete guide to using VLC as a media
player), the VLC Streaming HOWTO (a guide to using VLC as a streaming
solution), the VLS user guide and the VideoLAN FAQ.

Unfortunately, I don't know how to find these HOWTOs and guides.  I've done **find** searches for **vlc** and **videoLAN**, but haven't found this documentation.

Does anyone know where these HOWTOs will have been put?

---

### Post by lamalex on 2007-12-25
/usr/share/doc/videolan-doc/

---

### Post by t0p on 2007-12-25
Thanks lamalex!  I didn't know about /usr/share/doc... I'll definitely pay attention to it in the future though!

One thing I don't understand: I did a **find** search

```
find / videolan-doc
```

and it came back

```
find: videolan-doc: No such file or directory
```

But as there *is* a directory **videolan-doc**, shouldn't find have found it?

---

