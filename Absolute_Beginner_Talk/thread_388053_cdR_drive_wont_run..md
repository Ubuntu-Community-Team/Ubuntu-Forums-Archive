---
title: "cdR drive wont run."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-19
hey all. when attempting to load up a disc (any disc) into my cd rw drive i get this error.

```
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
```

```
mount: block device /dev/hdd is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdd,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so
```

any help?

---

### Post by twikletoes on 2007-03-21
after you try to mount it (mount /dev/hdd to wherever) and it comes up with the message that says 
                         
                               dmsg | tail
 type that. Then tell me what it says

---

### Post by belikralj on 2007-03-21
I believe twikletoes means

dmesg | tail

And also it could be useful to post your /etc/fstab file

---

### Post by leonid on 2007-05-15
I have the same problem although i have /dev/hdc /media/cdrom0 in the fstab file .. Also The message iget is:
[17187507.748000] UDF-fs: No fileset found
[17187507.876000] Unable to identify CD-ROM format.
[17187559.236000] UDF-fs: No fileset found
[17187559.320000] Unable to identify CD-ROM format.
If anyone outhere is capable of fixing the problem I would be grateful
Leonid

---

