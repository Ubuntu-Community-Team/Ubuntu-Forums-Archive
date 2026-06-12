---
title: "safe to unmount ntfs drive in tmp folder?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by aryn449 on 2007-07-04
Hi,

I just checked to see how much disk space I have on my Linux partition and realized that there was 9,5 GB in my tmp folder.  When I looked I realized it was my Windows partition.  How did this happen?  Is it safe to just unmount it?  or remove it?

It shows up as /tmp/disks-conf-sda1

Thanks!

---

### Post by jasonlfunk on 2007-07-05
Ubuntu detected and automatically mounted the disc. If you don't need it when in Ubuntu, you can unmount it. You can also comment it out of your /etc/fstab if you don't want it to mount anymore.

---

### Post by aryn449 on 2007-07-05
Thanks for your reply.

I tried to unmount the partition.  It doesn't appear in fstab.  It's being mounted in tmp/ .  I even tried disabling it in the disks menu (system --> administration --> disks).  It disabled it but then it reappears.  Any one else have a similar experience?  Any solutions?

Thanks

---

### Post by ekiepurnomo on 2007-09-23
this might will do

go
          sudo -sda1
you entered root, from there you can umount any NTFS (i think....)
go
          umout /dev/sda2

my window is detected as (C)SDA2 and (D)SDA5
i dont know what you done, but i assume you create 
mount point for your window partition, and that could only able to be umount
on ROOT

best regards

---

