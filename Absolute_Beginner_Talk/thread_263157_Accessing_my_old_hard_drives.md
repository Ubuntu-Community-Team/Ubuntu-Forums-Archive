---
title: "Accessing my old hard drives"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by spiritof1976 on 2006-09-22
Hi. I've just installed Ubuntu on my new computer.

I put some old hard drives into my computer, but I can't access any of the files on them because they're formatted for Windows.

Is there a way of accessing the files in them via Ubuntu? In particular there's a PowerPoint presentation in one of them that I'm especially keen to retrieve.

---

### Post by mejy on 2006-09-22
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows) should contain everything you need to know.

---

### Post by spiritof1976 on 2006-09-22
> **mejy said:**
> [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows) should contain everything you need to know.

Thanks, but that page seems to be assuming that the user has a windows partition. I don't have windows at all on my computer. Just Ubuntu.

---

### Post by bulldog on 2006-09-22
Make a mount directory in /mnt

sudo mkdir /mnt/backup

sudo fdisk -l 
to see your hdd and partitions

Choose the one you want to mount 

sudo mount -t ntfs dev/hd?? /mnt/backup

You should fill hd?? with what you want to mount.

Assuming you want to mount a ntfs partition.

---

