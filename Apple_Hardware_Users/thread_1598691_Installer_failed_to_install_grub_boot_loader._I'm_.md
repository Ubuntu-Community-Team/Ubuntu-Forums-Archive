---
title: "Installer failed to install grub boot loader. I'm trying to finish the install NOW"
date: 2010-10-16
forum: Apple Hardware Users
---

### Post by MountainX on 2010-10-16
Toward the end of installing Ubuntu 10.10 32bit (Alt CD) on my iMac 11,1, the installer asked me to type in the location for installing the grub boot loader. 

I told it to use /dev/sda3 and it immediately failed. I'm still in the installer. Can anyone suggest a solution?

Here are my partitions on sda:

  3.1 kb free space
#1 209.7 MB B EFIboot
#2 961.3 GB    hfs+
  1.0 MB free space
#3 1.0 MB  biosgrub
#4 46.6 GB etc4 for Ubuntu
#5 2.0 GB swap

...from the shell in the installer, there is no grub.cfg in /target/boot/grub.

What next?

---

### Post by MountainX on 2010-10-16
I went into the rEFIt partitioning tool. According to the GPT partition table, everything appears OK.
But there is a message:
Status MBR partition table is invalid. Partitions overlap.
ERROR: Not Found reported from gptsync.efi.

I do not see an overlap by looking at the table. Suggestions?

---

### Post by MountainX on 2010-10-16
I found this page:
[http://ubuntuforums.org/showthread.php?p=9984223#post9984223](http://ubuntuforums.org/showthread.php?p=9984223#post9984223)

After reading that whole thread, all I can say is that this looks hopeless.

This thread is not solved. I'm not sure how it got marked solved.

---

### Post by pc_michael on 2010-10-16
I think you'll need much more than a megabyte for /dev/sda3 if it's your /boot mount point.  I gave that partition 100MB and grub is currently using about 50MB of that (but that can grow).

Try resizing and then reinstalling grub, then if you still have problems with overlapping partitions, [this post](http://georgia.ubuntuforums.org/showpost.php?p=8146538&postcount=6) worked for me with gptsync.

---

### Post by MountainX on 2010-10-16
> **pc_michael said:**
> I think you'll need much more than a megabyte for /dev/sda3 if it's your /boot mount point.  I gave that partition 100MB and grub is currently using about 50MB of that (but that can grow).

Try resizing and then reinstalling grub, then if you still have problems with overlapping partitions, [this post](http://georgia.ubuntuforums.org/showpost.php?p=8146538&postcount=6) worked for me with gptsync.

Thanks for the link. That looks helpful -- but it also looks like a challenging task.

BTW, as far as what I had intended, sda3 was not for /boot. It's just for grub. And I was just following a set of instructions that have supposed worked for other iMac owners who want to install Ubuntu. On my PC I usually use 200 MB to 1 GB for /boot when I give it it's own partition.

---

### Post by srs5694 on 2010-10-16
> **MountainX said:**
> I went into the rEFIt partitioning tool. According to the GPT partition table, everything appears OK.
But there is a message:
Status MBR partition table is invalid. Partitions overlap.
ERROR: Not Found reported from gptsync.efi.

I do not see an overlap by looking at the table. Suggestions?

The GPT and MBR partition tables are separate. You said your GPT partitions look fine, but the message says that the MBR partitions overlap. In fact, this is a very common problem; the software that the Web pages say to use is buggy and creates this invalid hybrid MBR.

The easiest solution is to use Linux fdisk to delete the overlapping 0xEE partition (it's probably /dev/sda3 *in the MBR*). Alternatively, you could rebuild the hybrid MBR with a tool that doesn't have this bug, such as [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/).

---

### Post by MountainX on 2010-10-16
> **srs5694 said:**
> 
The easiest solution is to use Linux fdisk to delete the overlapping 0xEE partition (it's probably /dev/sda3 *in the MBR*). Alternatively, you could rebuild the hybrid MBR with a tool that doesn't have this bug, such as [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/).

Thank you. So, if I do the easy thing and delete /dev/sda3 (which is indeed the offending partition), will I then install grub to sda4?

I have not been able to boot my iMac with the Ubuntu LiveCD (or install from that disk) so that complicates things a little.

I was just reading about GPT fdisk at rodsbooks.com... lots of stuff to read... (and not enough time)

---

### Post by MountainX on 2010-10-17
> **MountainX said:**
> Thank you. So, if I do the easy thing and delete /dev/sda3 (which is indeed the offending partition), will I then install grub to sda4?


I did delete sda3 and I used the rEFIt partition tool and it reported success in syncing the partition tables and told me everything was OK. I installed grub via:
```
#grub-install /dev/sda4
```

It was successful.

But now, when I (attempt to) boot into Ubuntu, rEFIt tells me the operating system is missing.

---

### Post by Slinkee2k on 2010-11-10
Hi. Any more news on the missing OS issue? I suppose you figured it out by now.

---

### Post by linuxopjemac on 2010-11-10
I installed Grub on /dev/sda with a --force
It runs fine.

---

### Post by MountainX on 2010-11-10
> **Slinkee2k said:**
> Hi. Any more news on the missing OS issue? I suppose you figured it out by now.

No. I gave up installing Ubuntu on my iMac. Too many problems. Even if I had gotten it installed, the Magic Trackpad and Magic Mouse would not have worked well, so I decided it was not worth the trouble.

EDIT: This was my main problem (but obviously not the only problem I encountered). This one's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

I hooked up an external monitor and booted into a Linux LiveCD and verified that this is indeed the issue I'm having. 

Using options - radeon.modeset=0 nomodeset and installing via the Alt CD do not work around the issue for me.

---

### Post by Slinkee2k on 2010-11-16
> **MountainX said:**
> No. I gave up installing Ubuntu on my iMac. Too many problems. Even if I had gotten it installed, the Magic Trackpad and Magic Mouse would not have worked well, so I decided it was not worth the trouble.

EDIT: This was my main problem (but obviously not the only problem I encountered). This one's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

I hooked up an external monitor and booted into a Linux LiveCD and verified that this is indeed the issue I'm having. 

Using options - radeon.modeset=0 nomodeset and installing via the Alt CD do not work around the issue for me.

Thanks for the update. That's a bummer. I know the Ubuntu community is working to standardize--well, to update and add correct drivers as much as possible. I can say this: every new version is way more compatible than the previous one! ;)

---

### Post by MountainX on 2010-11-16
> **Slinkee2k said:**
> Thanks for the update. That's a bummer. I know the Ubuntu community is working to standardize--well, to update and add correct drivers as much as possible. I can say this: every new version is way more compatible than the previous one! ;)

Oh, I agree. I didn't say I gave up on Ubuntu. ;) I just gave up on installing it on my iMac. 

Being unable to install Ubuntu on my iMac, I set a goal to build a PC that was as quiet and fast as the iMac for the same price. (The iMac was much faster and way quieter than the Ubuntu PC I was using at that time.) 

In the end, I could not match the engineering elegance or the quietness of the iMac for the same price. But I did end up with a PC that is **faster and nearly as quiet**. This is my main machine now and it runs Ubuntu 10.10.

---

