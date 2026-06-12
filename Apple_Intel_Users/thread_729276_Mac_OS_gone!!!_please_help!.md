---
title: "Mac OS gone!!! please help!"
date: 2008-03-19
forum: Apple Intel Users
---

### Post by amaragon on 2008-03-19
Hi everyone,

I followed the directions to install Ubuntu on a MacBook Pro (the last model), and then after I reboot, grub didn't recognize that I had Mac OS also in the system. Now, I can boot only to Ubuntu.

I tried add the operative system to the /boot/grub/menu.lst but I receive weird error messages saying that I cannot start from that partition. I also tried options (hda,0), (hda,1), (hda,2) because I don't know where exactly is Mac OS located in the hard drive (should be the first one but it didn't work).

What should I do to have dual boot? Is there something that I can do to fix this? If not, how can I get the original configuration back?

Thank you all,

aa

---

### Post by cyberdork33 on 2008-03-19
you do not use grub to boot OSX... Hold Option while booting and you should be able to choose the partition to boot.

---

### Post by amaragon on 2008-03-19
Yeah! I was able to find fix the problem. It seems that I installed grub on top of refit??? Pressing option I went back to Mac OS and reinstalled rEFIt, then everything went smoothly. Now I have other problems though... thanks for replying.

aa

---

