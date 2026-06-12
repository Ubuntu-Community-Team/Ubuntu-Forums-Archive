---
title: "[SOLVED] How to share ext drive with Windows comp?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by phatjonny on 2007-07-02
Dear Forum,

Fantastic, what more can I say.  In less than a week I have gotten more out of this old laptop than I did with SUSE 9.3 in over a year...

OK, I bought an external harddrive 2.5 Samsung 80G in a housing and swapped it with the old 11G in my computer.  Installed ubuntu and am able to use the other drive by USB.  However, when I plug it into my girlfriend's computer Windows doesn't recognise a thing...

Now when I loaded both SUSE and ubuntu I used the full disc without making partitions.  Is this the root of my problem, and what should I do about it?

Cheers

John

---

### Post by testube_babies on 2007-07-02
2 options:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

I highly recommend the fs-driver.

---

### Post by phatjonny on 2007-07-02
Thanks for that.

So if I download one of those options on the other XP PC then It will have no problem reading files, I'll have to get her permission for that.  I have a flashdrive which is recognised by both computers.  Is there, by chance, a way to get a drive to function like that without the above mentioned download?

Cheers

---

### Post by derred on 2007-07-02
You could always install Ubuntu on her computer as well ;)

---

### Post by davidjmayo on 2007-07-02
What is the old 11G formatted as? ext2 or ext3?

I guess your flashdrive is FAT32
Both XP and ubuntu recognise and read/write to FAT32 as it doesn't have permissions
so format the old HDD as FAT32 and both OSes can use it

do this until later when 
> You could always install Ubuntu on her computer as well 

---

### Post by phatjonny on 2007-07-02
Yeah you are right it is FAT32.  Going to search how to format my disc now.
Thanks for help.

---

### Post by Bothered on 2007-07-02
Can the ext2 IFS for Windows be configured to permit only read access to the ext2/3 partition (rather than read and write access)?

---

### Post by fakie_flip on 2007-07-05
I just installed winblows to my second hard drive for a few games, and installed the ext2ifs driver. It did not find my ext3 partition on the first hard drive. Both hard drives are identical sata2 320 gb seagates. I am including a screenshot. Please help.

---

