---
title: "[SOLVED] Permissions on backup file"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by rmockler on 2007-09-30
Using Feisty Fawn - I have created an ext3 partition on my backup USB harddrive and did a chown to my username, and under Permissions it appears OK.  But, whenever I use partimage to backup my system,  the backup file is owned by root, and therefore inaccessible to me.  How can I create this file so that it is owned by ME?  Any help would be appreciated.
~Richard

---

### Post by Pumalite on 2007-09-30
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)
[http://www.aota.net/Script_Installation_Tips/changemode.php4](http://www.aota.net/Script_Installation_Tips/changemode.php4)

---

### Post by aysiu on 2007-09-30
Well, as far as I know, PartImage needs to be run as root, so if PartImage is creating a backup file, the file will also be owned by root.

---

### Post by bodhi.zazen on 2007-10-01
It is best your backup is ro and owned by root.

---

### Post by rmockler on 2007-10-01
I agree with the two above posts, but when I was earlier using partimage to backup to the fat32 partition, the backup file was owned by my username.  Once I created an ext3 partition, the backup file is now owned by root.  Will this cause any permissions problems if I restore the backup at a later date?  
~Richard

---

### Post by bodhi.zazen on 2007-10-01
Well, fat does not support linux ownership/permissions (they are set at the time of mount).

Not likely to be a problem, but I can not confirm this.

---

### Post by rmockler on 2007-10-01
Sounds good to me !!
~Richard

---

