---
title: "Changing Ntfs to Vfat without formatting drives"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2006-09-04
I got three partitions on my drive. All of them are ntfs. one of them is windows. I can temporarily remove my docs, in the other two drives. 

How do i convert my windows ntfs drive to fat32 without uninstalling windows or formatting the drive. I don wana lose my programs and settings. 

I would have a headache coz i got the huge list of programs and settings.

It would be interesting if ubuntu could do this!!!!

---

### Post by maelgwynffn on 2006-09-04
The answer is no.

That is because the way the information is installed.

Its easy to convert TO NTFS, but not FROM NTFS

But there may be a util that you can use.

Mael

---

### Post by iampoch on 2006-09-05
It's possible using a third-party software like Norton Partition Magic. But I do highly disagree with changing NTFS to FAT32.

Uh could I ask why you'd want to change your NTFS to FAT32?

---

### Post by manojvekaria on 2006-09-05
Coz ubuntu cannot install itself on a ntfs partition. it needs vfat or ext3 partition to work. 

Can i make a installation on a ntfs partition.

---

### Post by b_martinez on 2006-09-05
Even though Windows has a script to change an NTFS partition from NTFS TO FAT32, they warn you that it is not a good idea. To install into NTFS, you can use VMWare (I think) , but it'll cost money. Best way to do this is to free up soe space by shrinking an empty NTFS partition. First , on the win os, defrag the partitions, then back them up! When you install Ubuntu, only use the tail end of the hard drive, and shrink, not delete, the last partition. If possible, opt to install grub onto a floppy disk.
hth
Bill

---

### Post by manojvekaria on 2006-09-05
Thanx for that. It really helps me.

How do i mount the windows ntfs drives ones i have done the shrinking.

It displays the icons, but when i click on them.

error says: unable to mount.
How do i solve that problem????

---

### Post by iampoch on 2006-09-05
are you installing via the live cd? I had a Windows XP installed before installing Ubuntu.  My whole hard drive was set to NTFS.  Upon installation, i was asked how much space I'll allocate for Windows. After setting it, the installer automatically allocated an ext3 partition for Ubuntu and another 2gb for the swap partition. Try the Live CD first, I assure you, it'll install :)

---

