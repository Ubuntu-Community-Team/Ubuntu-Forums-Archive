---
title: "Mounting at startup"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by brander on 2006-11-20
Hi, as a newbie I am looking for the linux equivalent of autoexec bat to mount a logical drive at startup. With your help I have mounted many devices and the one I wanted most mounts with:

su
<pw> 
mount /dev/hda5 /mnt/Ddrive -t ext3
chmod -R 777 /mnt/Ddrive/

I see that the file required for this is /etc/fstab but examples for doing this involve extra switches like iocharset=utf8,umask=000 0 0

Are these really necessary or can I just put in the lines above which work in terminal? Thanks.

---

### Post by Bachstelze on 2006-11-20
They're necessary if you nned them :) If mounted them without parameters works the way you want, then don't add them.

(btw, iocharset=utf8 and umask=000 are the default parameters fot ext3 filesystems so it's useless to add them - they're more useful on FAT filesystems)

---

### Post by brander on 2006-11-20
nah, that doesn`t work. I need to know the exact text necessary and where it goes in the file.

---

