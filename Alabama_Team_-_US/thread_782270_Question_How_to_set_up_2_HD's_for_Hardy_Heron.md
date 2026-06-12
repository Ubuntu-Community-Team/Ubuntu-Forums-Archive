---
title: "Question: How to set up 2 HD's for Hardy Heron?"
date: 2008-05-04
forum: Alabama Team - US
---

### Post by MerlinsLair on 2008-05-04
In other words, what I'd like to do is to have one HD for my Home partition and the other HD for everything else. Unless someone has a better suggestion?

I'm aiming to keep my Home folder intact no matter what Distro I use or upgrade from later on. :)

---

### Post by tamoneya on 2008-05-04
where are you getting stuck:
1. Attach second harddrive to computer
2. Partition and format second harddrive
3. Add harddrive to /etc/fstab so that it is automatically mounted to /home

---

### Post by cyberdork33 on 2008-05-04
you don't even need a separate hard drive, just another partition.

sometimes the config files in home don't transfer well between distros... it may be a better idea to create a partition on the second drive and mount it somewhere like /media/storage and then make symlinks for the folders in your home folder like Music, Pictures, Videos.

---

### Post by crane on 2008-05-04
> **cyberdork33 said:**
> you don't even need a separate hard drive, just another partition.

sometimes the config files in home don't transfer well between distros... it may be a better idea to create a partition on the second drive and mount it somewhere like /media/storage and then make symlinks for the folders in your home folder like Music, Pictures, Videos.
Like he said, some thing won't work between different distros. I used to have a separate partition for my home but ran in this very problem. I finally just made sure I had a partition I used strictly for back-ups. Before I installed a new distro or updated the current one, I would back up my home directory to the set partition. then after install I could move the configs as I needed. I  eventually learned what i needed to back up and what I didn't.

---

