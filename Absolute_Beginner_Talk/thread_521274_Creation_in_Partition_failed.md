---
title: "Creation in Partition failed"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ben22 on 2007-08-09
Hello,

I manage to start Ubunutu with the live CD. When I want to install it now, I get the following error>

"The ext3 file system creation in partition #1 of SCSI 2 (0,0,0) (sda) failed."

What shall I do now?

adios,
ben

---

### Post by splintercellguy on 2007-08-09
Perhaps you can try manually creating the partitions in GPartEd, then selecting the partitions for setup.

---

### Post by sailor2001 on 2007-08-09
did you fefrag your drive first? I'm assuming you are trying to dual boot.

---

### Post by ben22 on 2007-08-09
I think there was an OS on the computer before. How do I get rid of it?

---

### Post by splintercellguy on 2007-08-09
GPartEd can let you do that. System -> Administration -> GPartEd I believe. If you want Ubuntu exclusively on the drive, you can really just delete all partitions and let Setup partition for you.

---

### Post by ben22 on 2007-08-09
> **splintercellguy said:**
> Perhaps you can try manually creating the partitions in GPartEd, then selecting the partitions for setup.

When I go to manual creation, and click on "new partition" I see the following:

"Type for the new partition: Primary Logical (Which shall I choose?)

New Partition size: 318721 MB (the drive is 300 GB big)

Location for the new partition: Beginning End (which shall I choose?)

Use as: ext3, ext2, reiserfs, jfs, xfs, fat16, fat32, swap, efi, dont_use (which one to choose?)

Mount point: no selection possible for ext 3"


Anyone can help (please consider that I am an absolute newbie!)

---

### Post by ben22 on 2007-08-09
> **splintercellguy said:**
> GPartEd can let you do that. System -> Administration -> GPartEd I believe. If you want Ubuntu exclusively on the drive, you can really just delete all partitions and let Setup partition for you.


how do I delet eall partitions - you mean with GPartEd ?

---

### Post by ben22 on 2007-08-09
Ok, when I try GpartEdit, I get the following error:

"the kernel is unable to re/read the partitiontables on the following devices: -/dev/sda

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access"

- What does unmount mean?
- how do I unmount?

thx

---

### Post by ben22 on 2007-08-09
Does noone know about this problem????

---

### Post by splintercellguy on 2007-08-09
Oh. Go to terminal and type sudo umount -a.

---

### Post by ben22 on 2007-08-09
> **splintercellguy said:**
> Oh. Go to terminal and type sudo umount -a.

what does "umount" mean?

---

### Post by splintercellguy on 2007-08-09
Unmount :).

---

### Post by ben22 on 2007-08-09
> **splintercellguy said:**
> Oh. Go to terminal and type sudo umount -a.

when I go to the terminal and enter to "ubuntu@ubuntu: ~$ "sudo unmount -a." "

 I get the error 

"sudo: unmount: command not found"

---

### Post by johnb820 on 2007-08-09
It's not 'unmount.' You should type in 'umount' without the n.

---

### Post by bjarneh on 2007-08-09
if you don't care for saving anything on the hard-drive (existing operating system and so on) then manual partitioning is not the way to go, just follow the standard setup tool, with its recommendations (ie. use entire disk for Ubuntu, and vipe out old stuff), that should work out...

---

### Post by ben22 on 2007-08-09
> **splintercellguy said:**
> Oh. Go to terminal and type sudo umount -a.

Okay, I wanted to thank everybody for the help. Got ubunutu running, a new member to the unbuntu community!

---

### Post by splintercellguy on 2007-08-09
Congrats. If you have any other issues, please create a new thread :).

---

