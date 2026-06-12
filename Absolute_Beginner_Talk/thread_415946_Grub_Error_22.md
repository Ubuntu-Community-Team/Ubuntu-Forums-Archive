---
title: "Grub Error 22"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by grEnAlEins on 2007-04-20
I installed on a new partition Ubuntu 7.04.  I heard that it had better wireless support than 6.10.  I ran the live cd, and then installed to a partition.  It was no better than my 6.10 (issue was partially solved with wireless on my 6.10 partition).  I used GRUB to delete the partition and grow my 6.10 partition.  Now when I boot it says Error 22.  I googled it, however it was not a help.  All of the solutions I saw required an XP startup disk.  Unfortunately, I lack said cd, and do not even have XP on that machine (came with Vista).  Is there anything that I can do to make my computer go back to booting 6.10 by default?  How would I go about doing this?

Thanks in advance,

Nick

---

### Post by markl187ld on 2007-04-20
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by grEnAlEins on 2007-04-22
Tried doing it with "hd0,1" and it did not like it at all.  But doing it to hd0 worked!  Thank you so much!  You, sir, are a gentleman and a scholor.

---

