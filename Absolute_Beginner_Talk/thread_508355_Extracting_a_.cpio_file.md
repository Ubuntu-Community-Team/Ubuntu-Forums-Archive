---
title: "Extracting a .cpio file?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-07-24
I have a .cpio archive that i need to extract. What command should i use to extract it?

---

### Post by lakris61 on 2007-07-24
Uh, have You tried cpio? ;)

To create archive:

ls > namelist
cpio -o < namelist >my-archive.cpio

To extract an archive:

cpio -i < my-archive.cpio

Look at man cpio (and info cpio)

Otherwise, any archive managing program or for example Midnight Commander, would be able to handle it, I guess.

/Lakris

---

### Post by bobbocanfly on 2007-07-25
Haha! Thanks. Linux is getting far too easy. I thought of trying a cpio command, but i thought hang on a minute, this is linux, must be something more complex.

---

