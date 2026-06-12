---
title: "root file system while dual booting"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-12
ok im trying to configure my partitions to install ubuntu feisty fawn 7.14 <-- i think that is the                         '                                                                                                            correct on,
but anyways im having trouble with the mount point.. i know im supposed to make it root file system but there is no option for that all i have is

/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

what do i put in to make it a root file system???:confused:

---

### Post by Raineer on 2007-07-12
/ is another name for "root"

---

### Post by mikewhatever on 2007-07-12
The first option is the root, so just put /.

---

### Post by tennvolsmb on 2007-07-12
ok first of all.... god im really retarded and second im now getting this error message 

The file system on /dev/sda3 assigned to / has not been marked for formatting. File systems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other file systems (/home, /media/*, /usr/local, etc.) may be used without reformatting.

i know i will probably feel retarded again but now what should i do?

---

### Post by Raineer on 2007-07-12
I'm pretty sure if you are using the live CD the graphical interface to partition the drives has a checkbox in the middle that says "Format?". 

I believe you either check that OR double-click the partition again to edit it, and there is a "Format?" box there.

You do need to format the root "/"  partition, Ubuntu will make you do this.  Others you don't "have" to but I choose to typically unless I'm replacing a Linux install with data I wish to keep.

---

### Post by tennvolsmb on 2007-07-12
see told you i would feel completely retarded... but thanks for all your help

---

### Post by mikewhatever on 2007-07-13
I really hope you do not chose to format the /media/* partitions. These are the Windows and, perhaps, storage partitions with all the data. Be very careful not to format them.

---

### Post by tennvolsmb on 2007-07-13
no i got it all working... i just wanted to upgrade it and so i just replaced the old linux partition with this new one

---

