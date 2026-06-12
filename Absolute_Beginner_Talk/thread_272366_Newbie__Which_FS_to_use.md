---
title: "Newbie : Which FS to use?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by 7mm on 2006-10-06
Hi there, I've got My Free UBUNTU CD. But before I start Installing it I must know what FileSystem to use. Must be Stable & High on Performance. Please Help Me People. Thank you.

---

### Post by angkor on 2006-10-06
The default ext3 has never given me any problems speed or stability wise. I'd say go for that one.

You can try these tweaks to boost speed on ext3 (at the cost of data safety).

[http://www.ubuntuforums.org/showthread.php?t=107856](http://www.ubuntuforums.org/showthread.php?t=107856)

---

### Post by mixmaster on 2006-10-06
ext3 is a very good all-round file system.  It may not be the best for a  specific task but it will generally cope well with all but the most extreme conditions.  More importantly, there are a lot of people around with a lot of ext3 experience ready to help if you have problems.

---

### Post by kerry_s on 2006-10-06
-> [http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

CONCLUSION
 For those of you still reading, congrats! The conclusion is obvious by the "Total Time For All Benchmarks Test." The best journaling file system to choose based upon these results would be: JFS, ReiserFS or XFS depending on your needs and what types of files you are dealing with. I was quite surprised how slow ext3 was overall, as many distributions use this file system as their default file system. Overall, one should choose the best file system based upon the properties of the files they are dealing with for the best performance possible!

---

### Post by Sef on 2006-10-06
> CONCLUSION
For those of you still reading, congrats! The conclusion is obvious by the "Total Time For All Benchmarks Test." The best journaling file system to choose based upon these results would be: JFS, ReiserFS or XFS depending on your needs and what types of files you are dealing with. I was quite surprised how slow ext3 was overall, as many distributions use this file system as their default file system. Overall, one should choose the best file system based upon the properties of the files they are dealing with for the best performance possible!

For newbies, I would recommend ext3, the Ubuntu default fs.

Me personally, I like reiferfs, but ext3 has supplanted it as the default fs on almost all major GNU/linux distros.  JFS and XFS are too quirky for a newbie.

---

### Post by 7mm on 2006-10-06
Thank you Members for your Suggestions. I'm very happy to recieve your thoughts. Though ut's been a while since I posted my problem (about 5hrs), I've already Installed UBUNTU 64-Bit on "ext3" FS. Sure I've followed your suggestions & pick "ext3". No problem Installing it, Fun though!:KS 

Thank you again to "angkor", "mixmaster", "kerry_s" & "Sef" for your Help.:D

---

### Post by mixmaster on 2006-10-06
> **7mm said:**
> Thank you Members for your Suggestions. I'm very happy to recieve your thoughts. Though ut's been a while since I posted my problem (about 5hrs), I've already Installed UBUNTU 64-Bit on "ext3" FS. Sure I've followed your suggestions & pick "ext3". No problem Installing it, Fun though!:KS 

Thank you again to "angkor", "mixmaster", "kerry_s" & "Sef" for your Help.:D
If you are genuinely a complete noob I would strongly suggest that you reinstall using a 32 bit version before you go any further.  You will see virually no performance gain with 64 bit for most usage scenarios and you are just making a lot of things more difficult for yourself.  Even the 64 bit gurus in the 64 bit forum admit this.

It is worthwhile upgrading the generic i386 kernel to the processor specific 686 or k7 kernels though and to pick up the smp options.

---

### Post by Echo35 on 2006-10-06
I usually use ext3, but I do reiserfs from time to time. I haven't noticed any performace difference between them, but maybe that's just me.

---

