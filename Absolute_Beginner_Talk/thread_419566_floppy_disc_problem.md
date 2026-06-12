---
title: "floppy disc problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by pecoronas on 2007-04-23
hello everybody,

i cant use the floppy in ubuntu 7.04.
if i put a floppy in, it won't read the content
if i drag and drop files in the floppy window, it won't write them on the disc.
the device is correctly plugged in (it works perfectly in windows and at boot).
how do i bring it to life?

---

### Post by insane_alien on 2007-04-23
try ```
mkdir ~/floppy
sudo mount -t vfat /dev/fd0 ~/floppy
```

it might work.

---

### Post by pecoronas on 2007-04-23
uhmmm... nope.
it returns this error:
mount: /dev/fd0 is not a valid block device

:confused:

---

### Post by pecoronas on 2007-04-23
update, after a reboot, i could access to the content of a floppy, which happened after a long noise, but then i couldnt change floppy or write on it. anyone can help? please note that the floppy drive works ok on windows

---

