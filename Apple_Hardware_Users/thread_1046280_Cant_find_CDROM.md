---
title: "Cant find CDROM"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by SNAFU0062000 on 2009-01-21
I am trying to install but when i get to detect HARDWARE it cant find CD ROM what should i do i am on a imacG3 slot loader Sys spec: 700mhz 1g ram and 60hd i did download the PowerPC alternate. what should i do

---

### Post by avtolle on 2009-01-21
Open another terminal by CTRL+ALT+F2, at the prompt type ```
sudo modprobe ide-scsi
```then return to where you were by pressing CTRL+ALT+F1, and click on the highlighted option. That fix is in the threads here as well. Good luck.

EDIT: Not click; sorry, you would press the Enter key to select the highlighted option. Some have reported that it takes more than one try.

---

