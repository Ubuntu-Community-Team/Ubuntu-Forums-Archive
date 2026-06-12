---
title: "How to uninstall Ubuntu?"
date: 2007-12-25
forum: Apple Intel Users
---

### Post by braveryonions on 2007-12-25
Well, I am dual booting with Leopard and Ubuntu 7.10.

Unfortunately, I am running out of hard drive space in Leopard. I want to delete my Ubuntu partition and make the Leopard one bigger to fill up the space where Ubuntu was. How can I do this?

---

### Post by jmagick07 on 2007-12-26
Did you use bootcamp or something else?  If you used bootcamp, then you can delete the partition you don't want within it, and it automatically adds that space back into one single partition.

---

### Post by braveryonions on 2007-12-26
No, I already tried boot camp. It won't work, because I changed the partition it made.

*poof* I just got an idea! If it works, I'll post it here.

---

### Post by IMcD23 on 2007-12-26
Hey,

Use iPartition to remove the partition if you can.  If you have an external hard drive, you can clone your os x partition to the external hd and then wipe clean the internal and clone it back over.  Good Luck!!!

IMcD23

---

### Post by braveryonions on 2007-12-26
Meh, my idea didn't work. I used the Ubuntu Live CD to delete the Ubuntu partition, and move the Leopard partition to be the first one. I then tried to use Disk Utility to enlarge it, but it didn't work. (Maybe the Live CD can enlarge it now? I'll try that!)

@IMcD23:
iPartition says it isn't compatible with Leopard. I don't want to pay either.

---

### Post by IMcD23 on 2007-12-26
Oh, i see, well i am out of ideas then, good luck!!!

---

### Post by Chayak on 2007-12-26
> **braveryonions said:**
> Well, I am dual booting with Leopard and Ubuntu 7.10.

Unfortunately, I am running out of hard drive space in Leopard. I want to delete my Ubuntu partition and make the Leopard one bigger to fill up the space where Ubuntu was. How can I do this?

Go to the disk utility in leopard and delete your ubuntu partition.  Resize and then enjoy, I don't know about the boot loader but you should be able to fix it with the leopard install disk.  Just make sure you have an up to date time machine backup just in case ;)

In a worst case scenario make sure time machine runs and completes the backup of all your files on an external then just wipe the entire disk and use leopard to recreate the partitions.  There is an option to restore from a time machine backup and I've found it works very well.  You get a fresh system install with all your files and programs pulled off of the time machine backup.

---

### Post by braveryonions on 2007-12-29
> **Chayak said:**
> In a worst case scenario make sure time machine runs and completes the backup of all your files on an external then just wipe the entire disk and use leopard to recreate the partitions.  There is an option to restore from a time machine backup and I've found it works very well.  You get a fresh system install with all your files and programs pulled off of the time machine backup.

Well, it looks like I'll need to do that. One question: if I do wipe the hard drive, how can I still use Leopard?

---

### Post by alpinesatan on 2007-12-29
im quite sure that if you boot up with the os x disc, you will get to the install screen, obviously dont install. 
And at the top click utility then disk utility. Here you can re format the linux partition back to NFS and you can also change the size of this partition too.
You might want a second opinion.

Kind Regards

Actually do get a second opinion just in case.

---

### Post by Chayak on 2007-12-30
> **braveryonions said:**
> Well, it looks like I'll need to do that. One question: if I do wipe the hard drive, how can I still use Leopard?

Sorry, I'm referring to the leopard install DVD put it in before you shutdown the system and then just hold "c" down as the mac boots again and it will boot off of the DVD.

---

### Post by cyberdork33 on 2008-01-02
you just need to use Disk Utility to delete the non-OSX partitions (use the little minus sign) and it will resize it to use the remaining space.

---

