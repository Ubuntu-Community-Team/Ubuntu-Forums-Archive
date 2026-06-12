---
title: "access slave hard drive"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by kwk_82 on 2007-01-10
I can't seem to figure out how to access my other hard drive. In the help menu it tells me to go to the drives section of the system menu and "mount" the hard drive but this option doesn't seem to exist. Any help would be much appreciated.

---

### Post by orb9220 on 2007-01-10
If the drive was there during the install it shoud be in /media/ folder. If you installed the drive after then you will have to edit your fstab.

For ntfs drive like your xp partition you can mount it as read-only.
If you have a fat32 you can mount it as a read-write

Open a term and enter 
gksudo gedit  /etc/fstab
will open your fstab for editing

Now my xp is the first partition on my first hardrive and is hda1 so fstab entry looks like this

/dev/hda1   /media/hda1 ntfs    defaults,utf8,umask=007,gid=46 0       0
which will show up on the desktop.
Look in your fstab and see if one of the lines has a nfts entry.

---

### Post by brandknewme on 2007-01-18
I have this same problem.

I want to add my slave 200gb, but I cant see it in media folder. It shows up in the device manger?

What is/How do you edit fstab?

---

