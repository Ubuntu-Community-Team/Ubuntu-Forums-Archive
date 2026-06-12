---
title: "How to set up a symbolic link"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by gollybegully on 2007-02-26
In the following How to for setting up a chroot [http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot)

He quickly breezes through at the end and says: "If you want to be able to easily launch 32 bit chroot apps from your 64 bit environment symlink the app name to /usr/local/bin/do_dchroot."

well how do i make a symbolic link?

---

### Post by bodhi.zazen on 2007-02-26
ln -s <existing_file> <link>

Example:

ln -s /mnt/data/music /home/user_name/music

creates a link in your home folder called "music" that is linked to the music folder on the data partition.

---

### Post by islander_810 on 2007-02-26
one more thing, there are two types of links, hard (ln -h) and soft/symbolic (ln -s). Always go for the latter

---

