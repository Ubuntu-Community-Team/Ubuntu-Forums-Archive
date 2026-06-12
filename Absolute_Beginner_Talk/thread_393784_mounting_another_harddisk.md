---
title: "mounting another harddisk"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by shashi123 on 2007-03-26
I have one xubuntu system but somehow its not able to boot so before formatting 
i want to back up the data 

but when i try to 

mount /dev/hda1 /mnt

it says u need to mention the file system 

plz help me out with this one as i need to backup the data

---

### Post by shashi123 on 2007-03-26
the exact message it gave was

mount: you must specify the filesystem type

---

### Post by AtrejuT on 2007-03-26
Well what file system is it - do you know? NTFS? Was it a windows XP plate before? 
If so try
```

mount -t ntfs /dev/hda1 /mnt/folder

```
Furthermore You should not really mount directly to /mnt but to a subfolder which you'll need to create in advance.

If you don't know which Filesystem it is, try
```

sudo fdisk -l

```
and post the output here.

good luck

atreju

---

### Post by cowlip on 2007-03-26
--atreju's reply was better and faster, ignore!-- :)

---

### Post by shashi123 on 2007-03-26
no it was xubuntu 6.10 so what could be the filesystem

---

### Post by AtrejuT on 2007-03-26
I'd guess ext3 (or possibly reiserFS).
So what does the above fdisk-command give?
Or start gparted, it should also be able to tell you

atreju

But since your real problem is that you can't boot from it this might also mean that the filesystem/partition table might be corrupted.
Try the above mentioned first anyways...

---

### Post by shashi123 on 2007-03-26
when i run 

 sudo mount -t ext3  /dev/hda1 /mnt

it gave following msg

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by AtrejuT on 2007-03-26
ok, so run gparted (probably you can just type gparted in a terminal, at least from a ubuntu live CD) and see what it gives. What does
```

sudo dmesg | tail
sudo fdisk -l

```
give?

---

