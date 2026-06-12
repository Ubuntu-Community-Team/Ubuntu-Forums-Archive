---
title: "Restoring WinXP bootability"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2007-03-01
Hi. My Windows is installed on hdb1, but it looks like some of it's boot file were on hda which is already formatted as ext3. The old familiar "non-system disk" message. Is there any way to restore WinXP bootability without reinstalling it? Thank you.

---

### Post by mikewhatever on 2007-03-01
Formatting as ext3 means Ubuntu is on that partition, and therefore there is GRUB somewhere around, right? If that's the case, you need to customise grub menu to boot Windows.
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by muxecoid on 2007-03-01
No, I tried it before and it did not work. :(

---

### Post by Dr. Nick on 2007-03-01
Does it boot into ubuntu? I dont think windows likes being on the 2nd hard drive, go into the bios and switch the hard drive boot order and see if it will boot straight into windows. 

Their is a way to have windows on the 2nd hard drive, but i never tried it

---

