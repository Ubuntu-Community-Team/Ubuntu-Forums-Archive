---
title: "modprobe error: No such device"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-28
This is just ticking me off.

$ sudo modprobe smsc47m1
FATAL: Error inserting smsc47m1 (/lib/modules/2.6.12-10-386/kernel/drivers/i2c/chips/smsc47m1.ko): No such device

However in the directory you can see that smsc47m1 *is* there:

$ ls -la
total 760
drwxr-xr-x  2 root root  4096 2006-03-24 21:32 .
drwxr-xr-x  5 root root  4096 2006-03-24 21:32 ..
-rw-r--r--  1 root root 17820 2006-03-11 11:42 adm1021.ko
-rw-r--r--  1 root root 20784 2006-03-11 11:42 adm1025.ko
-rw-r--r--  1 root root 46251 2006-03-11 11:42 adm1026.ko
-rw-r--r--  1 root root 22380 2006-03-11 11:42 adm1031.ko
-rw-r--r--  1 root root 26173 2006-03-11 11:42 asb100.ko
-rw-r--r--  1 root root  9657 2006-03-11 11:42 ds1337.ko
-rw-r--r--  1 root root 11407 2006-03-11 11:42 ds1621.ko
-rw-r--r--  1 root root  9918 2006-03-11 11:42 eeprom.ko
-rw-r--r--  1 root root 17874 2006-03-11 11:42 fscher.ko
-rw-r--r--  1 root root 18245 2006-03-11 11:42 fscpos.ko
-rw-r--r--  1 root root 20184 2006-03-11 11:42 gl518sm.ko
-rw-r--r--  1 root root 21805 2006-03-11 11:42 gl520sm.ko
-rw-r--r--  1 root root 29264 2006-03-11 11:42 it87.ko
-rw-r--r--  1 root root 13614 2006-03-11 11:42 lm63.ko
-rw-r--r--  1 root root 10539 2006-03-11 11:42 lm75.ko
-rw-r--r--  1 root root 12487 2006-03-11 11:42 lm77.ko
-rw-r--r--  1 root root 21538 2006-03-11 11:42 lm78.ko
-rw-r--r--  1 root root 21437 2006-03-11 11:42 lm80.ko
-rw-r--r--  1 root root 12877 2006-03-11 11:42 lm83.ko
-rw-r--r--  1 root root 37334 2006-03-11 11:42 lm85.ko
-rw-r--r--  1 root root 24137 2006-03-11 11:42 lm87.ko
-rw-r--r--  1 root root 17784 2006-03-11 11:42 lm90.ko
-rw-r--r--  1 root root 12789 2006-03-11 11:42 lm92.ko
-rw-r--r--  1 root root 11776 2006-03-11 11:42 max1619.ko
-rw-r--r--  1 root root 42463 2006-03-11 11:42 pc87360.ko
-rw-r--r--  1 root root  9628 2006-03-11 11:42 pcf8574.ko
-rw-r--r--  1 root root 11185 2006-03-11 11:42 pcf8591.ko
-rw-r--r--  1 root root  7858 2006-03-11 11:42 rtc8564.ko
-rw-r--r--  1 root root 20654 2006-03-11 11:42 sis5595.ko
-rw-r--r--  1 root root  8291 2006-03-11 11:42 smsc47b397.ko
-rw-r--r--  1 root root 11287 2006-03-11 11:42 smsc47m1.ko
-rw-r--r--  1 root root 22882 2006-03-11 11:42 via686a.ko
-rw-r--r--  1 root root 34362 2006-03-11 11:42 w83627hf.ko
-rw-r--r--  1 root root 38506 2006-03-11 11:42 w83781d.ko
-rw-r--r--  1 root root  9614 2006-03-11 11:42 w83l785ts.ko

This is extremely frustrating and I would appreciate some help.

Thanks,

---

### Post by paulmilliken on 2006-03-29
Todd,  Looks like you're not alone with this problem: [http://www.ussg.iu.edu/hypermail/linux/kernel/0505.3/1384.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0505.3/1384.html) and it appears that the kernel refuses to use that driver.  You might want to check your dmesg to confirm.

Paul

---

