---
title: "NTFS partitions"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by dijkstra on 2005-10-23
Hello!
How can i see the NTFS partitions in Ubuntu? My partitions are not windows partitions. They are only for data. I want to see those partition in Linux as i can see them in windows.

---

### Post by Snakey on 2005-10-23
[LIST=1]
[*]To mount Windows partition     sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
[*]To unmount Windows partition     sudo umount /media/windows/[/LIST]For more details, look @ [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by LHZ on 2005-10-24
Keep in mind that Linux can't write to NTFS. You'll be able to access and read all your files, but you won't be able to change them, or make new ones.

---

### Post by Moonbuzz on 2005-10-24
Thanks for the heads-up Snakey. 

When I installed Breezy it automagically found and mounted all my Windows partitions, which was absolutely the best move it could make, but it missed the NTFS partitions. I've changed the default details in fstub and now they load up as well.

---

### Post by Daniel Rehm on 2005-10-24
[QUOTE=Moonbuzz]When I installed Breezy it automagically found and mounted all my Windows partitions[/QUOTE]

Heh. I was actually just complaining about this feature in another thread.

---

