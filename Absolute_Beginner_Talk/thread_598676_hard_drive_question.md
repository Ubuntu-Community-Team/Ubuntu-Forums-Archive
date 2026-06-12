---
title: "hard drive question"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-10-31
how do i go and check the number of spin cycles my hard drive has done. is there a command you type into the terminal to see?

---

### Post by Jaco Du Toit on 2007-10-31
If you are referring to load cycles (the amount of times that the hard drive has been spinned up and down) then you need a package called smartmontools. Install it using:

```
sudo apt-get install smartmontools 
```

Then run

```
sudo smartctl -a /dev/sda
```

where you substitute /dev/sda for your hard drive. (Use df -h to check if unsure)

Your load_cycle_count should be there, and the value you are interested in is in the last column (RAW VALUE).

---

### Post by mramsey on 2007-10-31
Is it possible to use smartmon tools to check the status of an mounted network drive?

---

### Post by Jaco Du Toit on 2007-11-01
No I don't think so, since direct hardware level access to the remote drive is hidden by a network file system layer.

---

