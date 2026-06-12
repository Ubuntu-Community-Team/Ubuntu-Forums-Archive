---
title: "Partitioning issues?"
date: 2007-11-22
forum: Apple Intel Users
---

### Post by Spartan22x on 2007-11-22
Okay, I'm trying to install Gusty on my Macbook, and I'm running into some issues when trying to manually edit the partition table as instructed to by the wiki page.

Basically, what happens is I get an error telling me "The FATs don't match. If you don't know what this means, then select cancel, run scandisk on the file system, and then come back.". This shows up after I delete the /dev/sda3 partition and make a new ext3 partition and mount it as root. I don't know what it means but I don't know how to run scandisk on it either. All I really want to do is install gusty so that I can run Wine and stuff, but I don't want to **** up my leopard partition in doing so. Does anyone know what to do about this?

---

### Post by cyberdork33 on 2007-11-23
> **Spartan22x said:**
> Okay, I'm trying to install Gusty on my Macbook, and I'm running into some issues when trying to manually edit the partition table as instructed to by the wiki page.

Basically, what happens is I get an error telling me "The FATs don't match. If you don't know what this means, then select cancel, run scandisk on the file system, and then come back.". This shows up after I delete the /dev/sda3 partition and make a new ext3 partition and mount it as root. I don't know what it means but I don't know how to run scandisk on it either. All I really want to do is install gusty so that I can run Wine and stuff, but I don't want to **** up my leopard partition in doing so. Does anyone know what to do about this?

It has to do with the EFI partition. There is nothing wrong, Ubuntu just sees it strangely. Make sure it will not mount the EFI partition, and ignore the error.

---

