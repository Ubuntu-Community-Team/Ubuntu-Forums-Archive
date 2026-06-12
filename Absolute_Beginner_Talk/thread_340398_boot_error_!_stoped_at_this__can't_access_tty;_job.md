---
title: "boot error ! stoped at this : can't access tty; job control turn off"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by iblicf on 2007-01-17
after grub menu choice  , then boot process stoped with this notice  "can't access tty; job control turn off " 

within the "initramfs"  interactive environment  ... anybody any ideas ? 

i did "apt-get dist-upgrade"  last night ,  and choose a sleep button (shutdown disappear   ),then can not boot again, it seems something was wrong when the GRUB going to install kernel or initrd ,  anybody met this problem ever ?

what should i do in the rescue mode ? boot from live CD ? using grub ?

=====================================================
when i watch the boot progress this morning  by grub manually ,, first i think maybe the menu.lst point to the wrong device , but it seems accuracy,
then i fond from the screen display  , /sbin/init , /etc/inittab disappear ? odd ! been hacked ? or virus ? so the system stop the init progress 

i 'll try to copy these file from my liveCD ,hope it useful ,,maybe stupid ?

---

### Post by carlosfocker on 2007-01-17
Can you post what is displayed right from grub selection to this point and possibly anything after.

---

### Post by tommy1987 on 2007-01-17
I am having the same problem, see if your problems sound similar to mine, post titled "strange crash" in this forum.

---

### Post by JamieC on 2007-01-17
I had this problem when the menu.lst file was modified by GRUB. It was using the wrong value for 'root' in the kernel line.

---

### Post by iblicf on 2007-01-18
i have reinstalled  the edgy after all ,  
i try to copy the /sbin/init ,,,then boot again ,,,it  stop at another error  ,  use diff to compare the livecd/sbin  list  to my hd/sbin  ,,,boot still no work  , sooooo  strange , these file just disappear !!!

anyway , it took me to learn lot's of knowledge about  boot ..init ,gurb , and how to mount a squashfs -filesystem ,, :)
 
BTW , i fond that unbuntu got no /etc/grub.conf  and /etc/inittab !

---

