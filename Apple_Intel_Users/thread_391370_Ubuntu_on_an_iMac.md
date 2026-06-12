---
title: "Ubuntu on an iMac"
date: 2007-03-23
forum: Apple Intel Users
---

### Post by the.dark.lord on 2007-03-23
I got tired of OS X today, and decided to wipe out OS X, and install Ubuntu on this iMac(has Intel Core 2 Duo). Popped in my old Ubuntu 64 bit Ubuntu 6.06, and the installation went without a hitch. When I rebooted Grub displayed a message "Grub loading, Please wait...." forever. I couldn't figure out how to run Ubuntu without the live CD, Help please. Thanks in advance.

---

### Post by cyberdork33 on 2007-03-23
What process did you use (if any). Partitioning? rEFIt? etc

---

### Post by the.dark.lord on 2007-03-23
> **cyberdork33 said:**
> What process did you use (if any). Partitioning? rEFIt? etc

I just clicked on the 'erase all' button. No Partitioning etc.

---

### Post by cyberdork33 on 2007-03-23
Please post the results of 

```
sudo fdisk -l
```

Mac hardware is a little special. There are precautions. Especially in the area of partitioning. Macs have EFI instead of a BIOS and for this reason Ubuntu is not directly compatible. There are some extra steps required. For one thing, grub is not compatible with EFI.

See this page:
[https://help.ubuntu.com/community/iMacCoreDuo?highlight=%28imac%29](https://help.ubuntu.com/community/iMacCoreDuo?highlight=%28imac%29)

---

### Post by thonuz on 2007-03-23
Im running Feisty here (after wirless will ditch osx. Why arn't you running at least 6.10?

---

### Post by the.dark.lord on 2007-03-24
here are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30032   241232008+  83  Linux
/dev/sda2           30033       30401     2963992+   5  Extended
/dev/sda5           30033       30401     2963961   82  Linux swap / Solaris

---

### Post by the.dark.lord on 2007-03-24
> **thonuz said:**
> Im running Feisty here (after wirless will ditch osx. Why arn't you running at least 6.10?

Have to download it after I get Ubuntu 6.10 running. The connection is quite slow here. I'm glad to hear feisty doesn't have such problems, and I'll install it when it is officialy released. Know how to correct this GRUB problem?

---

### Post by cyberdork33 on 2007-03-25
Well apparently what you did *should* work. Try this thread:
[http://www.ubuntuforums.org/showthread.php?t=386545](http://www.ubuntuforums.org/showthread.php?t=386545)

---

