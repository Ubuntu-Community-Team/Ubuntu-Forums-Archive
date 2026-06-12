---
title: "Load screen wont show!"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-12-08
I did use live cd before i installed ubuntu 7.10 when i did use the live cd was i able to see the loading screen with the ubuntu sign and text.

Problem is now when i have installed ubuntu wont it show and booting the computer seem to take even longer then it took to boot up the live cd.

After some minutes do the login screen show up and everything work as normal.

any reason for this?

Can i disable the loading logo and get the text mode?

---

### Post by spiderbatdad on 2007-12-08
i had the same trouble, though it developed after a time on Gutsy. I followed instructions from another post and edited /boot/grub/menu.lst to look like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic 
initrd		/boot/initrd.img-2.6.22-14-generic

taking out " ro qiuet-splash etc.....

---

### Post by Teknyk on 2007-12-08
See the link in my sig

---

### Post by fain on 2007-12-08
I have this problem on my 8800 ultra video card i just put a no in front of splash to make nosplash in menu.lst. Looks ugly but it gets the job done. Also if on the live cd just hit f6 for more options and edit the line there.

---

