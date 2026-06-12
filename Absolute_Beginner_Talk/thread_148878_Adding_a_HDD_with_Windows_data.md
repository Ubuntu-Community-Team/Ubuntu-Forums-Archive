---
title: "Adding a HDD with Windows data"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by harry242 on 2006-03-22
Hi

I have an Ubuntu system and have since installed a second HDD with lots of data on it from when the PC was my Windows XP box.  So the file system is NTFS.  How can I (or simply is it possible) get Ubuntu to use this disk with the file system as it is?  Or do I have to back up the data and let Ubuntu re-partition/format and then remigrate the data?

Thanks
Harry](*,)

---

### Post by brandoncolorado on 2006-03-22
Hey,

I have a similar setup.  Search the forums for NTFS and search the repositories.  In Ubuntuguide.org:

Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?

---

### Post by brandoncolorado on 2006-03-22
Oh yeah,

That allows read only, 
write is in testing I guess, but it is at ubuntuguide.org too

---

### Post by animesh on 2006-03-23
writing on a NTFS system from ubuntu is not a good idea,convert your partition to FAT 32 (using Partition Magic) if you want to write on Windows partition

---

