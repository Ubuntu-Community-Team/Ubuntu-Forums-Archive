---
title: "A filesystem Linux and Windows can both read and write to"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by triple on 2005-12-25
I plan on having a 30GB-60GB partition that both Ubuntu and XP are going to be able to read and write to so I will be able to access some files between the two OSes. What is going to be my best choice to go about this? I don't know if I should jsut go with FAT32 or if there is a better choice.

---

### Post by estel on 2005-12-25
FAT32 is the best choice, unless you want to install something on Windows to allow it to rw your ext3 fs?

---

### Post by triple on 2005-12-25
[QUOTE=estel]FAT32 is the best choice, unless you want to install something on Windows to allow it to rw your ext3 fs?[/QUOTE]

I did not know of this. Is it stable and unlikely for data corruption? If Windows could read from ext3 reliably it would be great.

---

### Post by noob_Lance on 2005-12-25
make your ext3 and ntfs partitions... but also make like a 5gig fat32 partition for swapping files between linux and windows... i have a 40gig external HDD that came formatted as fat32.. so i jsut save all my stuff of that and go from there... works like a charm :)

---

### Post by mcduck on 2005-12-25
I never trust those apps that write non-native filesystems, so I'd use FAT32 to make sure that my files are safe.

---

### Post by triple on 2005-12-25
[QUOTE=noob_Lance]make your ext3 and ntfs partitions... but also make like a 5gig fat32 partition for swapping files between linux and windows... i have a 40gig external HDD that came formatted as fat32.. so i jsut save all my stuff of that and go from there... works like a charm :)[/QUOTE]

Ok, good idea. 

sup Ontario, Canada buddy 8)

---

### Post by dcraven on 2005-12-25
I would personally put my trust in Linux writing/reading from FAT32 long before trusting Windows to read/write from an ext3 partition.

HTH,
~djc

---

### Post by mistergq on 2005-12-25
I created a ext3 file system on a 5 gig partition to transfer files between the two operating systems.  I am using ext2 driver for windows that can be found at  [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) .  I know people trust fat32, but as I recall, Fat easily became defragged.  I will report back if any problems.

---

