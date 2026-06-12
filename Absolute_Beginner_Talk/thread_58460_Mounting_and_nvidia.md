---
title: "Mounting and nvidia"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by yootje on 2005-08-20
I have installed Ubuntu properly, dist-upgrade worked perfect, but I have 2 questions:

I can't reach any hd** in /dev/, should I mount them first? And should I configure fstab for future use? Where is that file anyway? :P

I have an on-board Nvidia Geforce MX 440. My screen resolution is 1600x1200, that's fine, but it's only 60 Hz. I've searched on the forum but there are so many thing, I don't understand exactly what I should do. Should I just install nvidia-glx? Or something else?

Thanks alot!

---

### Post by heimo on 2005-08-20
Yes, check your fstab. it's in /etc/fstab

Run* sudo fdisk -l* to list partitions.

Refresh rate*:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")


*) You can either reconfigure and select better matching monitor setup, or twark VertRefresh and HorizSync in xorg.conf (see linked post).

---

### Post by yootje on 2005-08-20
BTW, the other partitions are FAT32 partitions.

---

### Post by Lord Illidan on 2005-08-20
I suggest you click on the link in my sig..

---

### Post by yootje on 2005-08-20
The Hz problem is solved, I only need to mount the other partitions and ubuntu is ready  for me as my work-os! (thank god my soundcard works out-of-the-box ;) )

I think mounting I can handle by myself now, thanks everybody, especially Heimo!

---

