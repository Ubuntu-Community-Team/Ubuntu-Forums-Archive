---
title: "just did a reinstall now i'm getting strange errors"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2008-01-01
this is the output from dmesg grep (this is just partial as the output was huge!

[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 63
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 64
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 65
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 66
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 67
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 68
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 69
[  181.484000] mmcblk0: error 1 sending read/write command
[  181.484000] end_request: I/O error, dev mmcblk0, sector 70
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 63
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 64
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 65
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 66
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 67
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 68
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 69
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 70
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 0
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 8
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 16
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 24
[  181.488000] mmcblk0: error 1 sending read/write command
[  181.488000] end_request: I/O error, dev mmcblk0, sector 0
[  181.488000] mmcblk0: error 1 sending read/write command
[

---

### Post by taurus on 2008-01-01
Did you insert some kind of an external device like sd or something similar to that?

---

### Post by bradmayne on 2008-01-07
yeah that was it!

---

