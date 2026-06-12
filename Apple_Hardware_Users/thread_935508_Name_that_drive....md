---
title: "Name that drive..."
date: 2008-10-01
forum: Apple Hardware Users
---

### Post by explorer59 on 2008-10-01
Is it possible to name a hard drive so that it would be identifiable in the Macintosh Startup screen (power on/restart holding option key)?

---

### Post by Greettat on 2008-10-01
it is better to fight for good than to fail at the ill.-------------------------[evening dresses](http://www.china-stylish.com/Evening-Gown.html), [evening gowns](http://www.china-stylish.com/Evening-Gown.html), [wedding dresses](http://www.china-stylish.com/Wedding-Dress.html), [bridal gowns](http://www.china-stylish.com/Wedding-Dress.html), [wedding gowns](http://www.china-stylish.com/Wedding-Dress.html)

---

### Post by cyberdork33 on 2008-10-02
Not exactly sure what you are asking, but the drive name is not what makes it appear in the Startup Screen.

---

### Post by explorer59 on 2008-10-04
> **cyberdork33 said:**
> Not exactly sure what you are asking, but the drive name is not what makes it appear in the Startup Screen.

I'm not exactly sure what you are trying to say, but the words that appear below the button icons are the names that I have given to my Mac formatted hard drives/partitions.

Is it possible to to make the Linux volumes identifiable in the same way?

---

### Post by tgalati4 on 2008-10-04
Have you tried assigning volume labels using the Mac's Disk Utility?

---

### Post by explorer59 on 2008-10-04
> **tgalati4 said:**
> Have you tried assigning volume labels using the Mac's Disk Utility?

Yes, of course. Although GParted reports that there is an hfs partition on the drive, Disk Utility does not see it and can't identify the ext3 or swap partitions.

---

### Post by cyberdork33 on 2008-10-04
> **explorer59 said:**
> I'm not exactly sure what you are trying to say, but the words that appear below the button icons are the names that I have given to my Mac formatted hard drives/partitions.

Is it possible to to make the Linux volumes identifiable in the same way?

Sorry, I misunderstood what you were asking... Also would be helpful when asking questions to mention that you are on a PPC Mac...

---

### Post by explorer59 on 2008-10-04
> **cyberdork33 said:**
> Sorry, I misunderstood what you were asking... Also would be helpful when asking questions to mention that you are on a PPC Mac...

All the machines I commonly use are listed in my signature. That aside, for this particular issue, it is not relevant whether the machine in question is Intel or PPC.

It looks like iPartition might do the job, but I'm not prepared to fork out $50 unless I know for sure.

---

### Post by cyberdork33 on 2008-10-04
> **explorer59 said:**
> All the machines I commonly use are listed in my signature. That aside, for this particular issue, it is not relevant whether the machine in question is Intel or PPC.

It looks like iPartition might do the job, but I'm not prepared to fork out $50 unless I know for sure.Actually it does because the partitioning formats are completely different, and the machines in your signature are not necessarily the machine you are working with, I don't know either way. It just makes it easier to categorize the threads in this forum if you identify your hardware. Thanks.

---

### Post by tgalati4 on 2008-10-05
There are a few command-line ext2/3  label utilities.  e2label is one.  

sudo apt-get install e2label

---

