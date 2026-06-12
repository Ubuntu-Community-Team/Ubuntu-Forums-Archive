---
title: "[SOLVED] Restoring GUID scheme on disk"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by mariguango on 2008-05-12
Have a good day and night!

I have i strange situation.. 
I delete partition from partition editor on Ubuntu Live CD. Now in Leopard i can't get disk work correctly! Ok, explain - in Disk Utility i see my osx partition and 200 mb of free space. I can't add or delete partition, Options button disabled also.
In info i see that scheme of my disk is "master boot record". Ops..

How it's posible? And how i may restore GUID scheme on disk?

Be happy, and thank you.

---

### Post by cyberdork33 on 2008-05-12
> **mariguango said:**
> Have a good day and night!

I have i strange situation.. 
I delete partition from partition editor on Ubuntu Live CD. Now in Leopard i can't get disk work correctly! Ok, explain - in Disk Utility i see my osx partition and 200 mb of free space. I can't add or delete partition, Options button disabled also.
In info i see that scheme of my disk is "master boot record". Ops..

How it's posible? And how i may restore GUID scheme on disk?

Be happy, and thank you.
When the EFI partition gets deleted, the layout reverts to MBR. You have to restore the EFI partition at the beginning of the disk. I am not sure if gParted can create EFI partitions or not (They are essentially FAT32 with a special designation), and even then, I don't know if that would restore your GPT status.

---

### Post by mariguango on 2008-05-12
> **cyberdork33 said:**
> When the EFI partition gets deleted, the layout reverts to MBR. You have to restore the EFI partition at the beginning of the disk. I am not sure if gParted can create EFI partitions or not (They are essentially FAT32 with a special designation), and even then, I don't know if that would restore your GPT status.

Thank you for reply! 
Need advice in what i should use for this task (restoring EFI partition)?

---

### Post by cyberdork33 on 2008-05-12
> **mariguango said:**
> Thank you for reply! 
Need advice in what i should use for this task (restoring EFI partition)?You just need to create a EFI partition in the 200MB space at the beginning of the drive. I would suggest trying gparted, but there is no guarantee that will work. Sorry, I can't really give more specific details... I know there is an option to convert from a normal 'msdos' table to a GPT in gparted, but I think it requires wiping the entire disk.

---

### Post by mariguango on 2008-05-12
:guitar: :guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by mariguango on 2008-05-12
> **cyberdork33 said:**
> You just need to create a EFI partition in the 200MB space at the beginning of the drive. I would suggest trying gparted, but there is no guarantee that will work. Sorry, I can't really give more specific details... I know there is an option to convert from a normal 'msdos' table to a GPT in gparted, but I think it requires wiping the entire disk.

Thank you! You and guy from [this link]("http://www.ehmac.ca/anything-mac/43204-restore-efi-partition-proper-bootcamp-operation.html") - my today's BEST SUPERHEROES! THANK YOU \\:D/
Please take my best wishes of health and happiness.
:guitar:

Your both save me from per-sector raw scan of 750 Gb hdd.

---

### Post by cyberdork33 on 2008-05-12
please mark as solved

---

### Post by mariguango on 2008-05-12
> **cyberdork33 said:**
> please mark as solved

please tell me how?

---

### Post by cyberdork33 on 2008-05-12
> **mariguango said:**
> please tell me how?
Thread tools menu at the top of the page.

---

