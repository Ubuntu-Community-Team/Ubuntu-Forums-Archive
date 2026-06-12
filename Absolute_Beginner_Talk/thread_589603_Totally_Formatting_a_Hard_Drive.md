---
title: "Totally Formatting a Hard Drive"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2007-10-24
Hey guys,

I want to totally get rid of everything on my C:/ Drive, including my Windows installation. I then want to start over again but this time installing Ubuntu 7.10. My question is, how do I go around totally wiping everything from this drive. Any suggestions are appreciated. Thanks.

---

### Post by Rinzwind on 2007-10-24
No need for that.

You can selecte "use entire hard disc" during your Ubuntu install and that will do everything for you.
Or you can choose manual and play with your partitions (delete/merge/etc).

---

### Post by mojoman on 2007-10-24
> **Crumpets and Jam said:**
> Hey guys,

I want to totally get rid of everything on my C:/ Drive, including my Windows installation. I then want to start over again but this time installing Ubuntu 7.10. My question is, how do I go around totally wiping everything from this drive. Any suggestions are appreciated. Thanks.

Pop in the installation CD for Gutsy and follow the instructions. When you come to the 'partitioning' part you'll get some questions. Just answer 'use entire disk' and 'erase all contents' on the questions you'll get. It'll install Gutsy and erase Windows. Two for the price of one!

/mojoman

EDIT: A couple of seconds too late. Damn, this forum can be quick on support!

---

### Post by Sef on 2007-10-24
**Back up** any files that you want to have.

---

### Post by Crumpets and Jam on 2007-10-24
Thanks guys I didn't know that it would be so simple. Would the formating process be as easy on another drive that wasn't C: ? Would the CD give me an option to erase that?

---

### Post by steve.horsley on 2007-10-24
For drives you're not installing to, you would need to use gparted to delete the existing partitions. gparted is on the intaller CD, under System->Administration->Partiton Editor.

---

### Post by Crumpets and Jam on 2007-10-24
> **steve.horsley said:**
> For drives you're not installing to, you would need to use gparted to delete the existing partitions. gparted is on the intaller CD, under System->Administration->Partiton Editor.

Even if its a totally different drive? I mean, like a brand new one.

---

### Post by steve.horsley on 2007-10-24
Brand new drives don't have partitions that need deleting.

---

### Post by sneezymelon on 2007-10-24
you just need to format the brand new partition to ext3, ntfs or any other format according to your needs.
ext3 is for ubuntu file system
ntfs/fat 32 for data storage.

---

