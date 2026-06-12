---
title: "What does sda stand for?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-18
I know what hda is, and every example I see of  work being done to someone's computer they always use hda.hdb,hdc, etc. My installations always use sda and I'm not sure what the difference is. Can someone school me?

---

### Post by jvc26 on 2007-03-18
In my experience, the hdx# reference has been used for IDE Hard drives, whereas sdx# has been used for my sata drives. (The x corresponds to a, b, c etc. i.e. the different drives, and # corresponds to numbers 1,2,3 etc. used for the different partitions.)
Il

---

### Post by Bachstelze on 2007-03-18
s is for SCSI drives. This includes "pure" SCSI drives as well as most USB and SATA drives (your USB key will de detected as sdX too).

---

### Post by Arby on 2007-03-18
hda is used for IDE type hard drives. sda is used for SATA type hard drives. If Ubuntu is using sda on your system then it must be detecting that you have a SATA hard drive. As to what the difference between IDE and SATA disks is, that's beyond my level  of knowledge

---

### Post by 67GTA on 2007-03-18
Well that sounds right. I have a SATA -S.M.A.R.T hard drive. Thanks for the lesson.

---

### Post by 67GTA on 2007-03-18
I found a brief explanation of sata vs ide if anyone is interested.

[http://www.webmasterworld.com/forum105/319.htm](http://www.webmasterworld.com/forum105/319.htm)

---

