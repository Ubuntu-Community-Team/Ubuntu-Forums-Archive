---
title: "install mac os x on macbook alongside existing single-boot ubuntu?"
date: 2010-11-02
forum: Apple Hardware Users
---

### Post by npydyuan on 2010-11-02
I have installed Ubuntu 10.10 as the only OS on my Macbook 2,1's entire hard drive (used Live CD to reformat and install). Now I am wondering if it is possible to add a partition and install Mac OS X Snow Leopard alongside Ubuntu, for dual boot purposes. I have seen a lot of documentation for doing this the other way around--adding a Ubuntu partition to an existing Mac OS X installation, but I haven't found an answer for adding OSX to existing Ubuntu. If anyone knows anything about this, I would be most appreciative.

---

### Post by srs5694 on 2010-11-02
I've never done it that way, but in theory it should work fine. The worst that's likely to happen is that you'll need to fiddle around with boot loaders after you do it. Oh, actually, there's one caveat: If you used the Master Boot Record (MBR) partitioning system for your Linux installation, OS X won't install directly to that, so you'll need to convert to the GUID Partition Table (GPT) system. You can do this non-destructively with [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/) If you need to do that conversion, you may need to add an EFI System Partition, preferably as the first partition on the disk. If you're not sure what I'm talking about, open a shell, type "sudo parted /dev/sda print", and post the results here, ideally between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by npydyuan on 2010-11-02
Well, I *kind of* know what you're talking about, but maybe just enough to be dangerous. Here's the result:

```
Model: ATA Hitachi HTS72323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  314GB   314GB   ext4
 3      314GB   320GB   6290MB  linux-swap(v1)

```I assume this means I do not need to change the partition system?
When you say "fiddling around with boot loaders" I'm thinking something along the lines of how I've used rEFIt before to dual boot OS X and Linux.... or am I totally on the wrong train of thought here?

Thanks for your input!

---

### Post by srs5694 on 2010-11-02
You've got a GPT disk, so OS X will be happy with that. You will need to create an EFI System Partition, though -- or perhaps the OS X installer will do so if you just clear away enough free space for it and let it do its thing. The OS X installer is pretty inflexible about creating partitions, IIRC, so you might want to prepare them using Linux ahead of time. Using GParted, you can create a 200 MiB FAT partition and give it a "boot" flag (that's how GParted identifies an EFI System Partition); and create an HFS+ partition for OS X (you'll need to install an HFS utilities package; I don't recall its name offhand). Be sure to put 128 MiB of space around the HFS+ partition; OS X wants to see this or it might not install.

---

### Post by platz on 2010-12-05
I am really interested in the results of your experiment, I have almost the exact same situation and desire, to re-partition a single boot Ubuntu 10.10 MacBook Pro 2,1 for installing Snow Leopard. Any advice?

---

