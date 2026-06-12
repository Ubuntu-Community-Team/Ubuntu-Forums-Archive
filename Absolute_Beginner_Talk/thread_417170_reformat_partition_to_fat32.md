---
title: "reformat partition to fat32"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by hwheller on 2007-04-21
I have installed feisty to duel boot with Windows XP after removing my previous ubuntu partitions.  I used gparted from the live cd to delete the existing partition, then made a new partition of 32GB and tried to reformat it as fat32 so I can use it with both operating systems.  gparted refused to format it fat32.  I finally gave up, left the paritition in place, and installed feisty in the remaining empty space.  The installation went fine.  Now I again tried to reformat /dev/sda2 to fat32.  Both gparted and qtparted fail and say there is are mounted files.  I tried using umount /dev/sda2 without success.  

What do I have to do to the partition so I can change it to fat32?

---

### Post by shador on 2007-04-21
Hmm can't really help you with that. But have you tried maybe formatting in Windows? And what about NTFS? ntfs-3g is supposedly bullet proof and I've used it a while now with success.

---

### Post by z1p101 on 2007-04-21
You could use XP or use the mkdosfs command on the command line
I believe it is 
 mkdosfs  -F 32 /dev/[your partition] 
But I haven't done it in a while and you will most likely have to use sudo

---

### Post by hwheller on 2007-04-21
Thanks for the responses.  I now have a fat32 partition, but I don't know how it happened.  I repeatedly got failures when I tried with gparted and qtparted.  But this time when I logged on to Windows I found that I have a new drive E that is fat32.  In Ubuntu it also now is shown as fat32.  I can save from either system and read it from the other, so sometime or other the partition was changed, but the change was not acknowledged by the application doing it.

---

