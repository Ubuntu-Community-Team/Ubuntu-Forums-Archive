---
title: "problem with old home partition after reinstalling"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-22
Hello,

I had Ubuntu 6.10 till now, with dual boot (WinXP). I had home/shared data partition and another partition for "/". then, I reinstalled ubuntu, this time 7.04 and I only chose to reformat "/" partition hoping that home partition of 6.10 would be recognized by default. However, 7.04 made it's own home folder with user and desktop folders in "/" partitions. Now, everything is on "/" partition, which I of course don't like. Does anyone know how to switch the system to old home partition again?

---

### Post by zvacet on 2007-04-22
Did you use same username when you installed Feisty?Home and desktop are part of filesystem and of course you see them in root partition,but that is not point.Point is can you access your old home parititon?if you during installation used another user name, to access your old home partition add user with same user name as in Edgy.

---

### Post by mhansen on 2007-04-22
If I understand you right, you're going to have to edit /etc/fstab so that your original /home partition is once again mounted as it was....something like:

/dev/sda4 /home ext3 nodev,nosuid 0 2


should work. Of course, you're going to have to edit it depending on your system configuration.



Regards,
Mike

---

### Post by O-pos on 2007-04-23
It seems promising.

My home directory is sda3. sda4 is the partition where "/" is installed. so shoud I just write sda3 instead of sda4? yes, username is the same, but not password.

what shoud I type in terminal? no sudo .. mv... etc..?

---

### Post by O-pos on 2007-04-23
Somehow it didn't work well and I reinstalled "/" partition and in installer I also indicated to mount  old home partition as /home (by default it was going to be mounted as /media/sda3)

So, now everything is ok, but like  they say, nothing is perfect: this advanced wireless tool of 7.04, where you can see available networks, kind of disappeared and I can't find it. in "add to panel" I only found network monitor, which looks exactly as primitive as the one of 6.04.

Any ideas?

---

