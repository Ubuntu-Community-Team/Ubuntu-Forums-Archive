---
title: "mount dvd image"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by RonP on 2007-08-22
how do i mount a mdf cd image ?

---

### Post by kidcharles on 2007-08-22
If you don't already have a mount point in mind, do the following:

```

sudo mkdir /media/image

```

Then try:

```

sudo mount image.mdf /media/image -o loop

```

or substitute your mount point in for '/media/image'.

---

### Post by splintercellguy on 2007-08-22
You can't mount mdfs like that. You need something like AcetoneISO2.

---

