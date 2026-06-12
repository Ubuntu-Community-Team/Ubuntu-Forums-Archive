---
title: "Can't get partitioning to work out"
date: 2009-01-03
forum: Apple Hardware Users
---

### Post by stone915 on 2009-01-03
Hi, I'm trying to dual boot Ubuntu and OS X on my white Macbook, and I'm having some difficulties. The first time I tried, I used Disk Utility to repartition the drive, then used gparted to delete the new partition. However, when I ran the installer and attempted to select "use the largest continuous free space", the installer said that the entire hard drive would be converted to one big Ubuntu partition. So, I went back to OS X and repartitioned the drive into one big OS X partition and used Boot Camp to partition the drive. (I had read somewhere that Boot Camp was preferred over Disk Utility.) I rebooted Ubuntu from CD, ran gparted again and deleted the Boot Camp partition, and encountered the same problem when I ran the installer. The "before" drive is mapped as: free space 0%, /dev/sda1 0%, /dev/sda2 57%, free space 42%; and the "after" drive is mapped as Ubuntu 8.10 100%. Any ideas on why two different free spaces show up and why I can't install to the actual free space on my drive? Thanks!

---

### Post by Ruyuk on 2009-01-03
You have to use Toast Titanium. Try it.

(Not free but you can get a trail.)

Press the thanks button please!

---

### Post by stone915 on 2009-01-03
> **Ruyuk said:**
> You have to use Toast Titanium. Try it.

(Not free but you can get a trail.)

Press the thanks button please!

Why (and what) would the problem be with the CD? And how would Toast fix it?

---

### Post by pxwpxw on 2009-01-03
> **stone915 said:**
> Hi, I'm trying to dual boot Ubuntu and OS X on my white Macbook, and I'm having some difficulties. The first time I tried, I used Disk Utility to repartition the drive, then used gparted to delete the new partition. However, when I ran the installer and attempted to select "use the largest continuous free space", the installer said that the entire hard drive would be converted to one big Ubuntu partition. So, I went back to OS X and repartitioned the drive into one big OS X partition and used Boot Camp to partition the drive. (I had read somewhere that Boot Camp was preferred over Disk Utility.) I rebooted Ubuntu from CD, ran gparted again and deleted the Boot Camp partition, and encountered the same problem when I ran the installer. The "before" drive is mapped as: free space 0%, /dev/sda1 0%, /dev/sda2 57%, free space 42%; and the "after" drive is mapped as Ubuntu 8.10 100%. Any ideas on why two different free spaces show up and why I can't install to the actual free space on my drive? Thanks!

That is a mystery, but can you avoid the problem by choosing manual partitioning - you only need to make a new root partition in the free space, you can leave swap until after you install (or make say a 2 GB swap partition as well).

---

### Post by stone915 on 2009-01-03
> **pxwpxw said:**
> That is a mystery, but can you avoid the problem by choosing manual partitioning - you only need to make a new root partition in the free space, you can leave swap until after you install (or make say a 2 GB swap partition as well).

Awesome, thank you. I'll go try that and let you know how it works out.

---

### Post by stone915 on 2009-01-03
Sorry, I'm new at this and I don't want to mess up, so I'd like a clarification. By creating a root partition, do you mean that I should create an EFI boot partition?

---

### Post by mkvnmtr on 2009-01-03
It has been my experience on ppc macs that you should use the disk utility on your install disk to make your mac partition smaller. Then you don't make a partition or anything with the other space. Leave it as free space. Then when I install I choose to use the largest free space. Nothing more than that. A new user can get really messed up trying to follow advise on how to partition. Then just install.
One note I have seen that there is a bug in the installer for 8.10 where it will tell you that it is going to use your whole disk. That scares most people but it doesn't use the whole disk. It installs just like you want.
Another not on the later macs you use a different bootloader that I know nothing about. If you have any questions about that get answers from someone that is running your type of Mac.

---

### Post by pxwpxw on 2009-01-03
> **stone915 said:**
> Sorry, I'm new at this and I don't want to mess up, so I'd like a clarification. By creating a root partition, do you mean that I should create an EFI boot partition?

NO. EFI is all done automatically.

Using the installer partitioning step. It should show the free space you made. Make that a new partition, select ext3, use as '/',  that is the root partition for ubuntu.  Dont wory about swap.
It should go on show you what it is going to do.

---

### Post by pxwpxw on 2009-01-03
> **mkvnmtr said:**
> It has been my experience on ppc macs that you should use the disk utility on your install disk to make your mac partition smaller. Then you don't make a partition or anything with the other space. Leave it as free space. Then when I install I choose to use the largest free space. Nothing more than that. A new user can get really messed up trying to follow advise on how to partition. Then just install.
One note I have seen that there is a bug in the installer for 8.10 where it will tell you that it is going to use your whole disk. That scares most people but it doesn't use the whole disk. It installs just like you want.
Another not on the later macs you use a different bootloader that I know nothing about. If you have any questions about that get answers from someone that is running your type of Mac.

Do you have a reference to the bug, I did not see it here, I don't know if it is safe to proceed given that you don't want Macosx wiped out.

---

### Post by stone915 on 2009-01-03
> **pxwpxw said:**
> NO. EFI is all done automatically.

Using the installer partitioning step. It should show the free space you made. Make that a new partition, select ext3, use as '/',  that is the root partition for ubuntu.  Dont wory about swap.
It should go on show you what it is going to do.

Thanks a lot for all the help. I found a guide on the Ubuntu website that helped me with the manual partition, and it told me the same thing you just did. It's all installed and working well. Thanks!

---

### Post by mkvnmtr on 2009-01-03
PXWPXW I have seen that bug mentioned about 3 times here in the forum by people installing. Each time the installed and it was fine. On one post someone gave a reference to a bug report but I have no idea where to find a link. As I remember an install from long ago I thought it was saying it would delete all files. I believe it was just a language problem and  not a software bug.
But the good thing is this new user got his install going.

---

