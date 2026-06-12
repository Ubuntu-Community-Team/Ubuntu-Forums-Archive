---
title: "Printing with a KonicaMinolta 2400W"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by limbourg31 on 2008-01-11
There have been a few posts about installing the konica minolta 2400w so i decided to make a quick guide to help all you newbies out there :)

0. make sure that you have deleted all your previous printer installations

1. Download the code for the driver at [http://sourceforge.net/project/showfiles.php?group_id=108751](http://sourceforge.net/project/showfiles.php?group_id=108751)

2. Unpack the archive 
tar zxvf m2300w-<version>.tar.gz

3. cd m2300w-<version>

4. ./configure

5.sudo make

6. make install

7. Run the Printer Manager utility

8. Make sure the utility has selected your konica minolta 2400w

9. when it asks you for the driver, go to ./m2300w-0.51/ppd and install magicolor_2400W-m2400w.ppd

10. Finish it up with its name and location if you want

11. If it doesn't work immediately, restart ubuntu, and try running the printer again.

---

