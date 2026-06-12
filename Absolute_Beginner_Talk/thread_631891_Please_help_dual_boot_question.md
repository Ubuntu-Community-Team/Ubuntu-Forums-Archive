---
title: "Please help dual boot question"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by khgiese on 2007-12-04
This is my third attempt at installing ubuntu on my home PC.
I have 2 SATA drives. 
hd0 is my Windows XP partition
hd1 is the SATA drive I have ubuntu loaded on.
I set GRUB to (hd1,2) which should be the third partition on my second SATA drive.
I am now trying to create the ubuntu.bin file.
I do not have a floppy drive so I created a FAT32 partition I hoped to use for the file.
it would be listed as /dev/sdb2
the command I am trying to use is;
dd if=/dev/sdb3 of=/dev/sdb2 bs=512 count=1

But the last time I tried to use the /dev to define the output file location it messed up my hard drive partitons.

Am I entering the command wrong?
Is there another option I am not seeing?

Thanks in advance for any help,


khgiese

---

### Post by khgiese on 2007-12-04
Ok solved it my self. Ihave GRUB loaded on the Ubuntu partition, sdb3

My FAT32 directory is sdb2 
I then had to make what I guess is a virtual  forreference to the FAT32 by using the following command;
sudo mkdir /mnt/share

Then to link the virtual directory to my FAT32 drive;
sudo mount -t msdos /dev/sdb2 /mnt/share

Then i can execute the following to place the ubuntu.bin file on the FAT32 partition;
sudo dd if=/dev/sdb3 /mnt/share/ubuntu.bin bs=512 count=1

Now to test and see if I can use windows boot loader to boot ubuntu.

This way I can always remove the ubuntu partition and not affect my Windowsystem of have to go through the trouble of fixing the MBR.

---

