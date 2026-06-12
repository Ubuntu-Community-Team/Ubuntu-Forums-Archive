---
title: "Preserving timestamps during synce-pcp"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by t.septekin on 2007-09-05
Is it possible to preserve the timestamps while copying from a PC to a Windows CE device?
If not, can I do the equivalent of a "touch -d" to change the timestamp of a file in the PDA to my heart's content?

I have been working out some way of synchronizing a number of files which are duplicated in my laptop PC and iPAQ and which can be edited in either device. I can do this while updating the files in PC, preserving the original dates and times of the file in PDA, but when I update a file in the PDA the date-time assumes the current value. By the way, these are plain ordinary files, not Calendar or Contacts!

---

### Post by BobCFC on 2007-09-05
How are you copying to the device?

If you are using the normal cp command there is a switch to preserve the timestamps..


try:


```
cp -R --preserve=timestamps  /some/directory  /someother/directory
```

---

### Post by t.septekin on 2007-09-05
How can I access the Windows CE device (iPAQ1940) from the PC (hp pavilion ZV6245)?
The only way I know is by linking them via USB and using the synce program in the PC. To my knowledge synce does not allow ordinary cp, but requires its own synce-pcp routine.

---

