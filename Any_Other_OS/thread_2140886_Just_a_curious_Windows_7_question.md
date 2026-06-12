---
title: "Just a curious Windows 7 question"
date: 2013-05-01
forum: Any Other OS
---

### Post by shiman6 on 2013-05-01
I just repaired a computer with Win7 x64, using Ubuntu and gParted. The system's SYSTEM partition on the harddisk had some "bad magic" error (of course, computers run on magic) for NTFS or something, and i decided to just re-create SYSTEM as an empty partition, hoping that the windows recovery would recognize this and just refill it with whatever was in it before. As I was booting the system, i forgot to boot into the recovery CD and it just jumped straight into booting Windows 7... i had somehow fixed the issue. But now i'm wondering, what EXACTLY is the SYSTEM partition and what's on it?

---

### Post by iamkuriouspurpleoranj on 2013-05-01
Two texts from the MS site:

       1.

System partitions and boot partitions are names for partitions or volumes on a hard disk that Windows  uses when starting. These technical terms are  only important if you  have more than one operating system installed on your computer (often  called a dual-boot or multiboot configuration).

     The system partition contains the hardware-related files that tell a computer where to look to start Windows. A boot partition is a partition that contains the Windows operating system files, which are located in the Windows  file folder. Usually, these are the same partition, especially if you  have only one operating system installed on your computer. If you have a  multiboot computer, you will have more than one boot partition. An  additional term, the active partition, describes which system partition (and thus which operating system) your computer uses to start.

     When you turn on your computer, it uses information  stored on the system partition to start up. There is only one system  partition on a Windows-based computer, even if you have different versions of Windows installed on the same computer.   However,  non-Windows operating systems use different system files. In a multiboot computer using  a non-Windows operating system, its system files are located on its own partition, separate from the Windows system partition.

      A boot partition is a partition that contains Windows operating system files. If you have a multiboot computer that contains, for example, this version of Windows and Windows XP, then each of those  volumes are considered boot partitions.
[FONT=times new roman]
[/FONT]----

2.

**System volume**

  The system volume refers to the disk volume that contains the  hardware-specific files that are needed to start Windows, such as Ntldr,  Boot.ini, and Ntdetect.com. 

On computers that are running the Intel x86 line of CPU  processors and later versions, the system volume must be a primary  volume that is marked as active. This requirement can be fulfilled on  any drive on the computer that the system BIOS searches when the  operating system starts.

The system volume can be the same volume as the boot volume.   However, this configuration is not required.[B]

Boot volume[/B]

  The boot volume refers to the disk volume that contains the Windows  operating system files and the supporting files. By default, the Windows  operating system files are in the WINDOWS folder, and the supporting  files are in the WINDOWS\System32 folder. 

The boot volume can be the same volume as the system volume. However, this configuration is not required.

There is only one system volume. However, there is one boot volume for each operating system in a multiboot system.

---

