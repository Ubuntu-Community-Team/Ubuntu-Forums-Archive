---
title: "Mounting Changes the Mount Dir into an Unknown File"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by jbulcher on 2007-03-26
Hi!

This is my first attempt at mounting, and I am attempting to mount a windows share. I have smbfs installed (that was a problem initially), and the command I am using executes. However, when I attempt to browse the mount point using Nautilus, it lists what used to be the directory I was mounting to as an unknown file. ls -l at a command line tells me the same thing. After unmounting, it returns to a normal directory

Aargh! This is kind of frustrating. What am I missing? Here is the command I am using:

mount -t smbfs -o username=user //192.168.1.200/it /mnt/windows

and I type my password at the prompt. Oh yes, I am root when I do this.

I've tried to search for threads with this problem, but I'm really not sure what keywords to use. Thanks in advance for your help!

---

### Post by Cippa Lippa on 2007-03-26
Hei bulcher, is it a ntfs partition? in that case have you tried ntfs-3g. That is the standard solution for mounting the ntfs partitions.

have you checkee the /etc/fstab file? check that out and let us know what it says

Cheers

---

### Post by jbulcher on 2007-03-26
Hi Cippa!

Sorry, I guess I wasn't clear in my post. I'm trying to mount a network share, not a partition. Can you offer any suggestions for that?

Thanks!

---

### Post by jbulcher on 2007-03-27
I know it was only 15 hours since the last post, but bump... (This is kind of important to me)

---

### Post by Cippa Lippa on 2007-03-27
Hi JBulcher

I am sorry that I can't help you. I don't really know yet how linux handles networks...
Try other forums... somebody will hear you call for sure.

---

### Post by jbulcher on 2007-04-04
Thanks for trying, Cippa Lippa. I'll figure it out somehow.

---

