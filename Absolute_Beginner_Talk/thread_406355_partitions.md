---
title: "partitions"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-10
Hey, I found this on the net,
 
If you have a fast Internet connection and a CD burner, you can download the .iso image for System Rescue CD and burn it to a disk then boot from it. After it boots, at the prompt enter "startx" (no quotes) to start the GUI. Then run gparted (a partition manager). You can use it to resize, create, and remove partitions etc. This CD also includes partimage (a partition imaging utility) which can be used to create or
restore image(s) of your partition(s).

System Rescue CD contains many other utilities for system rescue as well. It is a complete Linux OS on a "Live CD". You can read the details on the WEB page I linked to above.

2). Boot from your Windows boot floppy (if you have one) and use fdisk to remove your partitions

If the partitions are removed, then can you install an OS system, regardless of what the OS is ? say Ubuntu and or windows? 

Thank you Sherri

---

### Post by rennen01 on 2007-04-10
Yes, System Rescue and GParted Live CD have saved my bacon on more than one occassion. :)

---

### Post by mi_were on 2007-04-10
> **delilahjed44 said:**
> Hey, I found this on the net,
 
If you have a fast Internet connection and a CD burner, you can download the .iso image for System Rescue CD and burn it to a disk then boot from it. After it boots, at the prompt enter "startx" (no quotes) to start the GUI. Then run gparted (a partition manager). You can use it to resize, create, and remove partitions etc. This CD also includes partimage (a partition imaging utility) which can be used to create or
restore image(s) of your partition(s).

System Rescue CD contains many other utilities for system rescue as well. It is a complete Linux OS on a "Live CD". You can read the details on the WEB page I linked to above.

2). Boot from your Windows boot floppy (if you have one) and use fdisk to remove your partitions

If the partitions are removed, then can you install an OS system, regardless of what the OS is ? say Ubuntu and or windows? 

Thank you Sherri


The simple answer is yes.

However you need to note that each OS will require that the hard disk be ready and able to be formatted. This means in the case of windows that the disk hard atleast one active (primary) partition! 

so despite removing all partitions you need to come back and create atleast one in this case a partition that is 100% of the space available on the disk. You don't neccessary have to format the partition windows will do it as you proceed through the installation process.

The same in principle applies for Linux it will also format the hard disk as you install it and create the partitions that it needs.

I hope that was helpful.

---

### Post by delilahjed44 on 2007-04-10
[COLOR="DarkRed"]Ok thank you for that, can you answer me this, how would I then come back and create a partition on the hard-drive at 100% as you say, how would I do this?

Sherri 
Thanks, and yes this is helpful.[/COLOR]

---

