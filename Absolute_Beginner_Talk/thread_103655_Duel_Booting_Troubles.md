---
title: "Duel Booting Troubles"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by yut3r on 2005-12-14
I just installed BREEZY on my IBM Thinkpad.  I needed to do a duel boot simply because I have to use some windows stuff for work.  The process went smoothly, but now I can't load windows.  My machine knows it is there, but can't launch.

Please help.

Thanks

---

### Post by Herman on 2005-12-14
yut3r, Hello,
> I just installed BREEZY on my IBM Thinkpad. I needed to do a duel boot simply because I have to use some windows stuff for work. The process went smoothly, but now I can't load windows. My machine knows it is there, but can't launch.

You should be able to use a GAG boot floppy disk or CD to boot Windows if you have to in a hurry, temporarily, for the time being. You'll find info on that in the GAG page in my signature link, (it's easy). 

Next, the best thing to do is to find out what your trouble is with GRUB exactly, and correct it. That is normally easy also, but it requires more information from your end. The kind of information that is needed is also explained in my signature link, on the GRUB Help page. 
More specifically, if you can let us know if it's a single hard-disk and IDE or SATA, and show us what your menu.lst file has on it to begin with, then someone will be able to help you. Other useful information would be details of your partitions obtianed by opening a terminal and typing ```
sudo fdisk -l
```, then in your reply, let us know what that says. :smile:  (Herman)

---

### Post by kingsidy on 2005-12-15
can u post what type of error you are getting? Another thing you can do is try reconfiguring GRUB. Make sure that you see windows in the GRUB list in the boot folder

---

