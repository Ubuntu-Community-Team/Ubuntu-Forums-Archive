---
title: "install problems"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by 88e28m5 on 2007-02-11
I keep trying to install ubuntu 6.10. I have tried both the desktop and the alternative. It hangs up at 46% creating ext3 file system for / in partion #1 of ide1 master (hda).

this is the system

Soyo 6bav5 440bx
nivida video card
512 meg of ram
80g hardive

????????

---

### Post by shareMenaPeace on 2007-02-11
Did you burn the CDs on lowest speed(4x)?

---

### Post by 88e28m5 on 2007-02-11
No I burn it at 24x

---

### Post by 88e28m5 on 2007-02-11
Had to switch to the other burner to get it to go down to 4x.

---

### Post by 88e28m5 on 2007-02-11
Ok burn at 4x  it went pass the 46% to 100% on the first partioning format. When it went to the second It hangs up at 33% creating ext3 file system for / in partion #1 of ide1 master (hda).

---

### Post by shareMenaPeace on 2007-02-11
Try again now format the missing 1.

---

### Post by 88e28m5 on 2007-02-11
i am not sure which option to use. Here is what I have

erase entire disk: IDE 1 master (HDA) 80.0 gb
use largest continous free space
erase entire disk and use LVM: IDE1 master (hda)
manually edit partion table

---

### Post by shareMenaPeace on 2007-02-11
> **88e28m5 said:**
> i am not sure which option to use. Here is what I have

erase entire disk: IDE 1 master (HDA) 80.0 gb
use largest continous free space
erase entire disk and use LVM: IDE1 master (hda)
manually edit partion table
Depends, if you have the complete HD free to use for ubuntu you can choose the first option.
If it during this stage hangs go to the last option and post the content from there.
basicly you need

1x ext3 as big as possible 
1x linux-swap 1gigabyte

You can later resize and make another partition.

---

### Post by 88e28m5 on 2007-02-11
I went ahead and downloaded 6.06 alternative to see how that would do. So far it is installing with no problems. Why do you think 6.06 install with no issue?

Will try 6.10 again later.

---

### Post by shareMenaPeace on 2007-02-11
Its another installer or something it is common suggested if the 6.10 fails.

---

### Post by 88e28m5 on 2007-02-11
Once again thanks. I will try again.

---

### Post by 88e28m5 on 2007-02-22
****

Ok I finally got 6.10 loaded. Everything works fine except I cannot get the network to work. The Realtek card is loded and DHCP is check. Still no internet connection.

---

