---
title: "[SOLVED] I made an error when I was partitioning during gutsy install"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by .nedberg on 2007-10-26
Hi

I recently installed kubuntu gutsy on my laptop. Everything is working perfectly. But I made a mistake when I shrunk my Windows partition. I wanted to give 20GB to kubuntu and leave the rest for Windows. But the result was the other way round. Could I just boot of the live cd and use gparted to resize the partitions without loosing any data? (I have already made a backup).

.nedberg

---

### Post by MegaJim on 2007-10-26
You can use the Live CD, but I'm not sure if the latest release supports ntfs partitions or not

If it doesn't you can download the latest GpartedLive or Parted Magic, both are reliable and stable, but it's always a good idea to have a backup.

As long as you haven't filled up the partitions its possible to resize them.

---

### Post by MegaJim on 2007-10-26
Double post

---

### Post by .nedberg on 2007-10-27
I just finished resizing the partitions.

I did the following:

Booted of the live kubuntu CD and started qtparted. For some strange reason qtparted could not resize the ext3 partition so I installed gparted with sudo apt-get install gparted.

In gparted I selected /dev/sda3 ("kubuntu partition") and resized that partition from 50GB to 20GB and moved it to the right. I then resized /dev/sda2 from 20GB to 50GB. I left /dev/sda1 unaltered (Dell rescue partition).

Gparted worked for about two hours and then told me everything was successful. And it was!

---

