---
title: "Permanent Deletion on 2nd HDD?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by AeroCross on 2007-11-05
I have this big issue. When I delete a file in the hbb1 HDD, it gets permanently deleted, instead of moving to the Trash Folder. What can I do to fix this? Is there any way to make that possible? The hdb1 it's a NTFS Partition.

Thanks to the Ubuntu Community in advance =)

---

### Post by Sturmeh on 2007-11-05
U sure it's not being sent to the hidden folder ".Trash-USER" ?

Press Ctrl-H in the drive in question, and a folder should show called ".Trash-USER" ( with USER as ur username. )

You can recover or permanently delete stuff from there...

---

### Post by hyper_ch on 2007-11-05
As it is a ntfs drive I don't know if the trash bin actually works. It might well be that it doesn't.

---

### Post by Sturmeh on 2007-11-05
No it work's, it just doesn't show up in the UI Trash...

You need to go to .Trash-USER and empty it manually... ( It still treats the files as if they were in the bin. )

---

### Post by erginemr on 2007-11-05
> **AeroCross said:**
> I have this big issue. When I delete a file in the hbb1 HDD, it gets permanently deleted, instead of moving to the Trash Folder. What can I do to fix this? Is there any way to make that possible? The hdb1 it's a NTFS Partition.

Thanks to the Ubuntu Community in advance =)

Also are you sure that you have enabled the "ntfs-3g" package (under Applications -> System Tools), so that Ubuntu can write to the ntfs drive?

I don't know if it creates a trash can under ntfs, but it definitely cannot, if it is mounted as read-only.

---

### Post by AeroCross on 2007-11-05
It indeed worked. I already had the NTSF-3G package installed, and I pressed CTRL+H and the Trash was there... I just didn't knew that one  =)

Thanks a lot n.n

---

### Post by Asobi on 2007-11-16
sweet, tnx

all those little tricks in linux/ubuntu. makes it frustrating but also fun :mrgreen:

---

