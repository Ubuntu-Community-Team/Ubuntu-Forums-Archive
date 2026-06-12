---
title: "Adjusting my Dual boot setup and want to make sure I am prepared."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Calash on 2007-08-02
My current system setup has 3 Operating systems on is
Ubuntu - My current main system
XP 1 - This is my old application setup.
XP 2 - This is my game setup

Since I have gotten use to Ubuntu I no longer need the application setup, however I can not completely get rid of my game setup as some games just do not run in Ubuntu.

So, my current plan is to merge the two XP partitions and reload it to have a fresh OS to work on.  However, if I understand correctly, this will change the MBR to only boot into XP.

My question is can I fix this with the Live CD or do I need to download the "Super GRUB" that I keep on reading about.  I am going to be careful in my partitioning so Ubuntu will be safe.

Thanks

---

### Post by Kobalt on 2007-08-02
Yes, you can [restore Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") from the LiveCD.

---

### Post by logos34 on 2007-08-02
windows will overwrite grub on the mbr, and you can restore grub either using supergrub or the[ ubuntu live cd]("http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett").

---

### Post by Calash on 2007-08-02
Thats what I thought, but I wanted to make sure.


Thanks for the info :)

---

