---
title: "Need Help Booting Ubuntu via Boot Camp"
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by da1bu on 2008-07-18
Hi. I just installed Ubuntu 8.04 64-bit via boot camp on my macbook pro following this guide:

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I installed it successfully and followed all the steps, but i can't boot into Ubuntu. rEFit is displayed upon start up and i select 'Boot Linux from HD', then it prompts me to insert a boot disk (CD). 

I can easily boot into OS X, just not Ubuntu.

Do i have to select 'Boot Linux from HD' then install it again - then i would have 2 installs of Ubuntu on my HD?

Any help appreciated. Thanks.

---

### Post by nudded on 2008-07-18
when in de rEFIt startup menu select the partitioning tool,
it will say it updated the mbr, typ y and let it do its thing, now it should work

---

### Post by da1bu on 2008-07-18
Thank you for replying, it now works.

Just a quick question, on the rEFit menu when the Linux is selected it says start partition 4. Should this be partition 4 / have 4 partitions?

If not is there any way i can delete the unneeded partitions?

Thanks.

---

### Post by nudded on 2008-07-18
gparted is the linux utility if i am not mistaking for this kind of job

---

### Post by cyberdork33 on 2008-07-18
what is the output of ```
sudo fdisk -l /dev/sda
```?

---

### Post by da1bu on 2008-07-18
4 partitions:

/dev/sda1  fat32
/dev/sda2  hfs+
/dev/sda3  ext3
/dev/sda4  linux-swap

sda2 is mt OS X partition.
sda 3 and 4 are my linux / swap partitions.

is sda1 required to boot? Plus if i wanted to delete the linux partition do i unmount them in GParted and erase with disk utility?

Thanks.

---

### Post by cyberdork33 on 2008-07-18
well i don't know why it says it is on partition 4 as it is clearly partition 3. The first partition is the EFI partition. 

There is nothing wrong with the partition table though and I would change anything. If you are asking about deleting Ubuntu, then you can just delete partitions 3 and 4 and get OSX to resize your OSX partition to fill the space.

---

### Post by da1bu on 2008-07-18
Thanks, i'll leave things as they are for the moment and brush up on Ubuntu as I'm a new user.

Great support, cheers.

---

