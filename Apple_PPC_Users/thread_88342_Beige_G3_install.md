---
title: "Beige G3 install"
date: 2005-11-10
forum: Apple PPC Users
---

### Post by misguidedute on 2005-11-10
Semi succesful install of Ubuntu on a Beige G3
When I get to the end of the install I hit esc and then select a shell.
From there I try to mount my HFS partition however I have no success.
Instructions that I have found indicate that I want to mount /dev/sda5
My Mac partition is on partition 5 so this makes sense
I have created a directory in /target called hfs
mount /dev/sda5 /target/hfs -t hfs
and also tryed this with hfsplus
I get an error that the device doesn't exist
However in /dev there is nothing named sda of any sort

Is there  a way to tell what partitions there are and what the system has named them?
fdisk -l ifn't recognized
df does show me the mounted drive 
Which is /dev/scsi/host0/.......
there is also a /dev/scsi/host1/.......
The first one is the mounted drive per df
the second one looks like it might be the hfs partition so I tryed it as well no luck

At the end of the install I also get a message to set the boot directory as
root = /dev/sda8
on reboot it comes up with a kernel panic that sda8 doesn't exist and asks me to enter a valid path.

Can anyone assist me on this please?

---

### Post by ristosu on 2005-11-10
Are there devices named hda, hdb, hdc, etc.? Disks hanging on scsi-bus are named sd... and disks on ide-bus hd... My Beige G3 has both hard disk and CD drive on ide-bus.

---

