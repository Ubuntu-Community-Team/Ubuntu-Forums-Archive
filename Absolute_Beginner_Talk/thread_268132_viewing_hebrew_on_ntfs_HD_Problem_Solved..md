---
title: "viewing hebrew on ntfs HD Problem Solved."
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Fimget on 2006-09-29
Hello all,

I got a friend's laptop with damaged HD.
The guy used WinXP and now gets BSoD both on boot from HD and CD...
now, he really in need of the info on the disk and wants me to get it for him. I got a Win machine running FTP Server and can connect the laptop to my network.
so I was thinking to myself: "why, but a live CD would do the trick"
I got DSLinux and Ubuntu (little choise there....)
I booted from the CD and mounted the HD, but here the plot thickens... for the file names are in hebrew (0_0) and I can't get to read them... I guess this is because of the filesystem (NTFS)...
Is there some way to get those files?

thanks all.

---

### Post by Fimget on 2006-09-30
Heh, NVM

# mkdir /hd
# mount -t auto /dev/hda1 /hd -o utf8

solved the problem...:tongue:

---

