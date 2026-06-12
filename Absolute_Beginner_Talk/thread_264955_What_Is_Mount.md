---
title: "What Is Mount?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-09-25
when i install ubuntu it requires to mount such files as "root" "swap" etc. What does those kind of words meen?

---

### Post by kidders on 2006-10-03
They are conventional names for common disk partitions. Every Linux system needs a root partition ... someplace to regard as the "bottom" of the directory tree.

Additionally, most people create a swap partition, for use as virtual RAM (pagefiles), for performance reasons.

---

### Post by tonyr1988 on 2006-10-03
Basically . . . you know what partitions are, right? It splits your hard drive up into smaller parts. However, by booting into an OS, you don't automatically get access to all the different partitions. You have to first "mount" them so that you can read / write from them. <== That's what mounting (in general) means.

Now, for the specific type that you're talking about: Ubuntu has a lot of files in the "root" file system. Like kidders said, it's just the bottom of your directory tree. If you'll look at Ubuntu's file system after you install it, you'll see lots of folders, like:

/bin
/boot
/dev
etc etc etc

You can find out what those are here:

[http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard#Directory_structure)

You can put those folders into different partitions and "mount" them when you start up Ubuntu so you can use them like normal.

Why would you put them in different partitions? You may want to put your /home directory (with your personal files / configurations) into a different partition so that it's case if something happens to Ubuntu.

Sorry for ranting. I hope it wasn't too long (and I hope I wasn't wrong about any of that - I'm still fairly new to Ubuntu, too).

---

