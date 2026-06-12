---
title: "/dev/hda: No such device or address"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Mwelsh on 2008-01-16
I'm trying to copy a hard drive image from my /dev/hda across a network. I PXE booted the client that has the image I want so that it's not running on the image and therefore should be accessible. However, for some reason, the kernel I have for the PXE does not have the sudo command, but I should have root power and access.

However, here's the problem:

```
dd bs=64k if=/dev/hda | nc ****.****.****.**** ****
/dev/hda: No such device or address

```

and on the Server:

```
nc -l -v -p **** | dd of=/tftpboot/imagetest.file bs=64K

```

A lot of commands don't work on the kernel I have, and there is no vim or nano editor. I'd appreciate any help!

Thanks a ton

---

### Post by mikewhatever on 2008-01-16
Perhaps you need to specify a partition like /dev/hda1.

---

### Post by Mwelsh on 2008-01-16
I don't want a partition, and sadly I've realized my problem. PXE booting my client with the kernel I have erases any image on any hard drive. So I can boot it, but then the image I want is gone :P Thank you though

---

