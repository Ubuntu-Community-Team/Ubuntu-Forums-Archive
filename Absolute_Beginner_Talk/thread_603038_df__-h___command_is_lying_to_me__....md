---
title: "df  -h   command is lying to me  ..."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-04
I don't get a reasonable result from the du -h command.

For example, consider:

$ df  -h  /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3              92G   85G  2.2G  98% /


From the above, the result should be 7G -- not 2.2G. 
It gets worst.  I know I deleted four 16GB vmWare virtual machines and that space does not show up in the results.  I really should have over 60GB free in the / partition.

System -> Administration -> System Monitor shows my / on /dev/sdb3 as:

ext3  91.7GB total, 6.8GB free, 2.2GB available, and 2.2GB available.

Note:  I've emptyed the Trash Can too.

Anyone else note this?

Carl

---

### Post by rudeboyskunk on 2007-11-04
Did you reboot your computer after emptying the trash cans?

I usually don't trust df (I don't even add the -h option).  I would try Applications>Accessories>Disk Usage Analyzer.

---

### Post by cwmoser on 2007-11-05
Yes I did reboot and its still the same.

Carl

---

### Post by cwmoser on 2007-11-05
Could this be the reason for the output appearing to be the way it is:

I have a /home partition that is mounted  --  could that be factored into the results?
When I run Disk Usage Analyzer, I get:

  /  = 417.2GB
  /media  = 324GB
  /home  = 75.2 GB

When I subtract the size for /media and /home from /, I get:
  417.2  -  324  -  75.2  =  18  GB utilized by Ubuntu operating system.


Does this seem correct?

Carl

---

### Post by cwmoser on 2007-11-05
I found out what happened -- the files I deleted were in /root/.Trash.

Now,    df -h /    reports 69G free

Carl

---

