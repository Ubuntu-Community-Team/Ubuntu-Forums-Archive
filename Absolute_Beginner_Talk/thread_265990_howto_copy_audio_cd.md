---
title: "howto copy audio cd"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-26
Hello,

can anyone please help me to copy an audio CD? I followed the instructions from the dapper wiki:

sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024

but it doesn't work for me. In /dev I have /dev/cdrom, /dev/cdrw and according to the disk manager my cd is on /dev/hdc. No matter which one of those I take as if= I get the same "Input/Output error". So how can I do this  if possible without installing an extra application?

Cruz

---

### Post by colo on 2006-09-26
Use `cdrdao`. Its manpage will tell you how to do it.

---

### Post by Cruz on 2006-09-26
There is a secret command for everything isn't there? :) It worked great thank you!

---

