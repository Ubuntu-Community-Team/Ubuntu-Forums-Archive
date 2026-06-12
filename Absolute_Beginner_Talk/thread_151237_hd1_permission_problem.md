---
title: "hd1 permission problem"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by liorsolomon on 2006-03-27
Hi everyone,
I'm new to linux and esspecialy to ubuntu dist.
Once I intstalled it (went so smood and clear!) I found that my XP OS is mounted automaticly and I can reach it through /media/hd1
Today I installed a big update(not really sure what was it about) and that caused my grub to have another option for ubuntu on the OS selection when the computer boots(just a different version) and now if I try to reach my /media/hd1 I get this error:
"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "hda1"."

Any ideas????
Thanks
:-k

---

### Post by aysiu on 2006-03-27
Try this:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by pbaehr on 2006-03-27
I'm not sure about the permission problem but if you're interested you can clean up grub by editing /boot/grub/menu.lst. Do so cautiously, though.

---

### Post by akiro.yamamoto on 2006-03-27
Verify the correct entries in your /etc/fstab file.
See the ubuntu wiki or the Help on your system for mount instructions for Windows Partitions.
The extra entry is for the new kernel you installed during your update.
Hope this info helps ;)

---

### Post by liorsolomon on 2006-03-27
Thanks everyone the link to the mount windows article did the job
Thanks a lot:D

---

