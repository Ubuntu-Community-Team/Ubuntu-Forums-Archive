---
title: "how do i restore files?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-07-14
went thru some insanity in ubuntu, system wouldnt boot looked everything found a code entered it system boots now YAY! but all the files in my home folder are gone.  anyway to restore?

---

### Post by Brunellus on 2006-07-14
if you've deleted them...then no.  there is no way to restore.

If you used nautilus to 'delete' them, they are likely still in the trash.

---

### Post by maddbaron on 2006-07-14
looks like i deleted them. there isnt a norton ghost type program for ubuntu?

---

### Post by Brunellus on 2006-07-14
there is no 'undelete' functionality in the ext3 filesystem.  If its' gone...it's gone.

---

### Post by bruce89 on 2006-07-14
> **maddbaron said:**
> looks like i deleted them. there isnt a norton ghost type program for ubuntu?

No.  One of the problems with the file system which is default in Ubuntu (ext3) is that it is extremely difficult to recover files if they are deleted off the disk.  Source - [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Have you checked your ~/.Trash directory? (It's hidden, so you will have to press Control+H to show it).

---

### Post by maddbaron on 2006-07-14
> **bruce89 said:**
> No.  One of the problems with the file system which is default in Ubuntu (ext3) is that it is extremely difficult to recover files if they are deleted off the disk.  Source - [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Have you checked your ~/.Trash directory? (It's hidden, so you will have to press Control+H to show it).

well all my setting are still here so it didnt revert completely altho wine is here my wine installed programs are gone. and my desktop looks like the generic kde one, my gaim and kopete logs r gone but the programs i installed are there. my swiftfox reverted so time to do that all over. gosh. gotta search for how to backup system. but anyway how do i check the ~/.trash?in konsole?

---

### Post by maddbaron on 2006-07-14
ok ran in terminal. was told no dir existed so they r all gone.

sigh....

---

### Post by edoardo on 2006-08-09
boot from windows (*) and run this freeware
[http://www.adrc.net/data_recovery_software/](http://www.adrc.net/data_recovery_software/)

it's hard to find non-commercial undelete sw. this did the job for me. excellent stuff!

(*)assuming your data is more valuable than OS-religious beliefs of course  ;-) 
seriously, forensic has to use best-of-breed tools ..

---

### Post by crackers on 2006-08-13
Are files that are on the hard drive lost if I reinstall ubuntu? Had power outage couple of days ago and it appears that Ubuntu crashed. will not boot and have a bunch of error messages about files not clean and hda1 read only. So if I reintall ubuntu from the cd are the files that are currently their still be their after reintall?

---

