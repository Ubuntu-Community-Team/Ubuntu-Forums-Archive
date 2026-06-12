---
title: "Need a little guidance"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Zhrakkan on 2007-01-01
Greetings all.

I am a systems admin for windows, so I know that well.
I dont know linux.

So I wanted to install linux on one of my three computers to force me to get a little more familiar with it.

I wanted to start with what I needed and someone might be able to give me a little more guidance on the path forward.

This new Linux System need to do the following:
1)  Attach to a WINDOWS XP box to print (the printer is attached to the windows box)
2)  Host a data folder where the other Windows XP systems can access it (I have a large drive that I use as a poor mans backup, and they dump their data to this system)

What are your thoughts?

Thanks in advance from a person who is really trying to move forward and learn, and Ubuntu seems nicely done.

Zhrakkan

---

### Post by pay on 2007-01-01
Use a fat32 partition so then both the windows box and linux box can read the data drive that you needed and try samba for the network.

---

### Post by Sef on 2007-01-01
> Use a fat32 partition so then both the windows box and linux box can read the data drive that you needed and try samba for the network.

You could also use ext2 or ext3 instead of FAT32.

---

