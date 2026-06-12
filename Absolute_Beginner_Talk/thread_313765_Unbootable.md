---
title: "Unbootable"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by DrRootabega on 2006-12-06
I recently installed Ubuntu Edgy with great success.  I liked it so much that I thought I'd move all my documents and media to the ext3 partition.  Since i dont have enough free space to do this in one step, I did it in stages.  I moved about 4 gigs to the ext3 partition and then resized both the ntfs and ext3 using Norton's partition magic.  After it did its little thing, it rebooted, but i got an error in GRUM, error 17.  I can't get past the error screen.  Just about the only thing i can do is boot from the Edgy Live CD.

Did i mess up my partitions doing this operation and is it possible to fix the partition and boot record?

---

### Post by burek on 2006-12-06
> **DrRootabega said:**
> I recently installed Ubuntu Edgy with great success.  I liked it so much that I thought I'd move all my documents and media to the ext3 partition.  Since i dont have enough free space to do this in one step, I did it in stages.  I moved about 4 gigs to the ext3 partition and then resized both the ntfs and ext3 using Norton's partition magic.  After it did its little thing, it rebooted, but i got an error in GRUM, error 17.  I can't get past the error screen.  Just about the only thing i can do is boot from the Edgy Live CD.

Did i mess up my partitions doing this operation and is it possible to fix the partition and boot record?

resizing ext3 is risky  a bit maybe

to restore the grub in ur master boot:
live cd
cd /boot 
...
check the man
grub-install

---

### Post by aidanr on 2006-12-06
try the [super grub disk]("http://supergrub.forjamari.linex.org/")

---

### Post by DrRootabega on 2006-12-06
Can someone please explain in detail how I can install super grub on a usb hd, the directions that come with the files are somewhat unclear.

---

### Post by adrian15 on 2006-12-11
> **DrRootabega said:**
> Can someone please explain in detail how I can install super grub on a usb hd, the directions that come with the files are somewhat unclear.

Can't you wait 6 months for me for releasing a GOOD SGD release for the usb drives?

The current one is not very good one although it has the Restore Grub to MBR option handy.

Let's see. You copy paste the instructions. You quote them here in this forum and you tell me what do you do not understand. And I'll try to explain it better.

After that I will update the explanation.

Waiting for your questions.

adrian15

---

