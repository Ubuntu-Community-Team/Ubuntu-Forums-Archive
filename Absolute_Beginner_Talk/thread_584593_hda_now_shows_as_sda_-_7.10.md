---
title: "hda now shows as sda - 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-10-21
Just curious - why does my configuration seem to show a serial ATA drive (it's showing up as sda) since the installation of 7.10, when in fact it is a parallel ATA drive that used to show as hda?:)

---

### Post by TeaSwigger on 2007-10-21
Hello, yeah it's perfectly ok - a change in the kernel actually. It's using the SCSI driver now for IDE as well. No idea why though. :)

---

### Post by hyper_ch on 2007-10-21
wasn't that already the case in 7.04?

---

### Post by duckville on 2007-10-21
Yep, this was the case since 7.04; it caused a lot of pain & sleepless nights... ( a little over the top).
But all seems well with 7.10 in that respect.

---

