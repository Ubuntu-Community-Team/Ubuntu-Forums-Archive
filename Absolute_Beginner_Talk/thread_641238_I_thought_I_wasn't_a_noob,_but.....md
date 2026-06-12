---
title: "I thought I wasn't a noob, but...."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Hashi on 2007-12-15
Hi all,
    I just attached a previously used hard drive to my laptop, using an ide->usb caddy. Everything mounts ok, and that's good. However, I cannot do ANYTHING with the existing partitions, one NTFS and one ext3.
   I have tried parted and gparted, and both recognize the partitions, but I cannot change them. What's the go? In (swearword) XP I could just format them, and all would be well. What do I have to do to make one large (200gb) , empty partition?
   This should be easy, but I can't find a way to it??????
   Please help!!
Hashi
   PS I am running ubuntu 7.10.

---

### Post by daimaru on 2007-12-15
you will have to unmount the drive before you are able to format or edit it with gparted. umount  workd for me the rightclick unmount option in gparted did not work for me. so use terminal.

---

### Post by Paqman on 2007-12-15
I don't think you can make changes to a partition when it's mounted can you?

---

### Post by Hashi on 2007-12-15
Ah, you may very well be right. But how does (g)parted know that the disk exists if it's not mounted? Anyway, I will try and see waht happens.

Thanks heaps!
Hashi

---

### Post by Paqman on 2007-12-15
Dunno. You could always temporarily plug it into your machines IDE connectors to do your formatting if you can't see it through the USB ports.

---

### Post by oskar2000 on 2007-12-15
I've never used gparted... is there no error?
Doing it from the command line isn't much more difficult

umount [dev]

fdisk [dev] 
-> to change the partition table

mkfs-whatever [partition] 
to format the partition.

There are a gazillion tutorials out there.

---

### Post by ugm6hr on 2007-12-15
> **Hashi said:**
> Ah, you may very well be right. But how does (g)parted know that the disk exists if it's not mounted? Anyway, I will try and see waht happens.


GParted has an option to unmount drives (right-click on partition in question).

Then it should do what you ask.  I have had issues with an NTFS USB HD refusing to allow any resizing etc of partitions because GParted claimed that it could not read certain parts of the drive.  Not sure whether that's a reflection of the degree of fragmentation (it's my backup HD, so has never been defragged).  I was thinking of trying GParted LiveCD, but I don't really need to make partitions anyway.  I think I'll just leave it as a single NTFS partition for now.

---

