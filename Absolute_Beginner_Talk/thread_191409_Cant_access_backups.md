---
title: "Cant access backups"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Rent-A-Hero on 2006-06-07
Howdy

This is my first time on linux. I installed ubuntu just to see what it was all about and I happen to like it. Before I installed I backed up tons of files, in windows. Now I cant access all these backups in linux, some of the volumes dont show up and the one that does says "Unable to mount". I have no idea what I am doing and now I am sad.

Also, I tried to get back into windows. Its gotten corrupted, even though I installed ubuntu on a different drive. yay!

Can anyone point me in the right direction?

---

### Post by kaamos on 2006-06-07
Have you tried through System->Administration->Disks->partitions->browse ?

Your windows installation is most likely ok since ubuntu does not even know *how* to write to ntfs. The changes have most likely been on the boot record (where ubuntu installed the boot loader grub). If you get very desperate and need windows back, you probably can boot with a windows install cd, go to the recovery console and use the command "fixmbr". This removes the linux bootloader though. :(

---

### Post by Rent-A-Hero on 2006-06-07
Oh NOW I see them. But now I get a message saying that I dont have permissions. Whats all that about?

---

### Post by kaamos on 2006-06-07
It is a security thing. The installation makes the other volumes available only to the root user by default. You can get permission with "gksudo nautilus". The mounting behaviour can be changed by editing the file /etc/fstab

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by wthanna on 2006-06-07
Hi. I just have a moment to post a quick reply.  At the top of page in this forum, you will see a link to "Official Wiki".  Go there and do a search for "mount". You will find instructions on how to mount your partitions. They will vary depending on whether you are trying to mount a FAT32 partition, or NTFS partition, etc.  ..like I said, I just had a quick moment to post, so can't go in to much detail.. hope this helps.. will check back later to see how you made out.

---

### Post by Rent-A-Hero on 2006-06-07
YES! it works! You people are my personal heros. Thank you.

---

