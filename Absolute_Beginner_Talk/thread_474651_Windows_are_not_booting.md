---
title: "Windows are not booting"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Comcon on 2007-06-15
Hallo,
First of all i have two hard disks. 
Recently i had install Ubuntu on my second one which is slave.
But yesterday i though that it would better if i had installed Ubuntu on my first one which writes at 7200 rpm unlike my second which writes at 5400 rpm.
So i format my second with [B]disk manager[B] but i left the Linux-swap partition unattached.
Now when i open my computer it is showing the following  massage:
GRUB Loading stage 1.5.
GRUB Loading,please wait
Error 17
What i should do?
Thanks

---

### Post by Comcon on 2007-06-15
I have resize my second disk to ntfs and again it is not working
thanks

---

### Post by hoges on 2007-06-15
It would appear that you have erased the operating system. Error 17 means that it can't be found where it's looking for it.

Linux swap is just like temporary ram. It's for program memory that doesn't fit into the ram. ie if you load a game, all the data for it might overrun here.

Formatting is basically erasing. You have wiped it from the system

Also, ntfs is a windows file format. Using this will mean that linux will currently read and write to it, but not very well.

What did you use to format it? There may be something salvagable from it. Was ubuntu on the drive you formatted or on the other one?

---

### Post by Comcon on 2007-06-15
i use the disk manager.I formated the second with ntfs type because i wanted to use it as a storage disk for windows and i wanted to install again the Ubuntu on my first one.
Then i tried to get into the windows(without install the Ubuntu on my first disk) and it showed this massage :GRUB loading stage 1.5,
Error 17
Thanks

---

