---
title: "mount fat32"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-09-29
how do i mount my hard disk partitions if they are fat32? my partiotions used to be ntfs but i changed them to fat32 and all of a sudden all my data seems to have disappeared

---

### Post by Ben Sprinkle on 2006-09-29
Come on now...you already made this thread, look down some.
I answered.

---

### Post by mendingo84 on 2006-09-29
yeah but it was deleted

---

### Post by Ben Sprinkle on 2006-09-29
[http://ubuntuforums.org/showthread.php?t=267884](http://ubuntuforums.org/showthread.php?t=267884)

---

### Post by mendingo84 on 2006-09-29
yeah, sorry
i just saw that! my bad

---

### Post by orb9220 on 2006-09-29
you have to also edit your fstab. Open term and enter
gksudo gedit /etc/fstab 
Then find where the ntfs line is a change it to vfat
Example
/dev/hda1  /media/hda1     ntfs    defaults,utf8,umask=007,gid=46 0      0
would become
/dev/hda1  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0      0

---

