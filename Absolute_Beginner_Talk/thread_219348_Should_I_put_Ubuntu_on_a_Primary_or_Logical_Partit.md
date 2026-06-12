---
title: "Should I put Ubuntu on a Primary or Logical Partition"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by GfW on 2006-07-19
My computer has 2 hard drives. One drive has Windows, it is a Primary partition and the status is Active. The other drive is for Ubuntu (my first linux install) and it is an Extended Primary partition and is not Active.

If I install Ubuntu to the Extended Primary not active partition, will I be able to dual boot with Lilo or Grub?

Sorry if it's a really basic question.

Many thanks.

Fred

---

### Post by Skia_42 on 2006-07-19
As I understand it you have 2 **seprate** partitions, the primary partition and the extended primary partion. If that is true then yeah, you should be able to dual boot with Lilo or Grub. If you have any trouble tell us. Oh, If I were you I'd backup everything on your Windows Partition just in case something were to go wrong.

---

### Post by moshuptrail on 2006-07-19
Ubuntu is very flexible.  I've installed it on a second Primary partition with XP in the first primary partition (you can define up to 4 priamry partitions on a single drive), and in a logical partition in an extended partition.  I've used ext2 and ext3.  The only thing I noticed was that the install seemed much slower to an ext3 drive.
Other than that, no problems.

---

### Post by GfW on 2006-07-19
Thanks gentlemen but I have 2 separate hard drives.
Hard Drive 1 = 1 partition with Windows
Hard Drive 2 = 1/2 of hard drive is partitioned for Windows and the other 1/2 is partitioned as ext2.

Hard drive 1 is the active hard drive primary.
Hard drive 2 is Logical for the Windows partition and Primary for the ext2 partition.

[COLOR="Red"]If Windows is on Hard Drive 1 and Ubuntu is on Hard Drive 2 will LILO or Grub still perform the boot management fucntions[/COLOR].

I completly understand your answers and they have provided valuable info ... now I need the answer to the question up above.

Many thanks.

---

### Post by Orval on 2006-07-20
Yes, they will. What you want is exactly the configuration I have.

---

### Post by GfW on 2006-07-20
Thank you.

---

