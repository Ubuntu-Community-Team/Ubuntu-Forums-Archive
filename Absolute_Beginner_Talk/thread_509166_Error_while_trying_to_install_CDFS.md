---
title: "Error while trying to install CDFS"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by John Macnab on 2007-07-25
Hi folks
I'm trying to install CDFS on my system hoping it'll help with my VCD's not being recognized in Ubuntu.(The DVD's seems to be playing okies).I downloaded the file and am trying to follow the instructions- but when I type in the make command I get the following error. Could someone kindly tell me what could be wrong?

:~/Desktop/cdfs-0.42$ make
cc  -I/usr/src/linux/include -O -Wall -c audio.c 
In file included from audio.c:26:
cdfs.h:20:25: error: linux/types.h: No such file or directory
cdfs.h:21:25: error: linux/errno.h: No such file or directory
cdfs.h:22:26: error: linux/malloc.h: No such file or directory
cdfs.h:23:22: error: linux/fs.h: No such file or directory
cdfs.h:24:25: error: linux/locks.h: No such file or directory
cdfs.h:25:24: error: linux/init.h: No such file or directory
cdfs.h:26:25: error: linux/cdrom.h: No such file or directory
cdfs.h:27:26: error: linux/iso_fs.h: No such file or directory
cdfs.h:28:24: error: linux/time.h: No such file or directory
cdfs.h:29:27: error: linux/proc_fs.h: No such file or directory
cdfs.h:30:26: error: linux/string.h: No such file or directory
cdfs.h:31:25: error: asm/uaccess.h: No such file or directory
In file included from audio.c:26:
cdfs.h:89: error: expected specifier-qualifier-list before ‘time_t’
cdfs.h:97: error: expected specifier-qualifier-list before ‘mode_t’
cdfs.h:114: error: expected declaration specifiers or ‘...’ before ‘off_t’
cdfs.h:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cdfs_constructtime’
cdfs.h:129: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:129: warning: its scope is only this definition or declaration, which is probably not what you want
cdfs.h:130: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:131: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:132: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:133: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:135: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:137: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:139: warning: ‘struct super_block’ declared inside parameter list
cdfs.h:140: error: expected declaration specifiers or ‘...’ before ‘size_t’
cdfs.h:140: warning: ‘struct inode’ declared inside parameter list
cdfs.h:142: warning: ‘struct page’ declared inside parameter list
cdfs.h:142: warning: ‘struct file’ declared inside parameter list
cdfs.h:143: warning: ‘struct page’ declared inside parameter list
cdfs.h:143: warning: ‘struct file’ declared inside parameter list
cdfs.h:144: warning: ‘struct page’ declared inside parameter list
cdfs.h:144: warning: ‘struct file’ declared inside parameter list
cdfs.h:145: warning: ‘struct page’ declared inside parameter list
cdfs.h:145: warning: ‘struct file’ declared inside parameter list
cdfs.h:147: warning: ‘struct page’ declared inside parameter list
cdfs.h:147: warning: ‘struct dentry’ declared inside parameter list
audio.c:27:27: error: asm/byteorder.h: No such file or directory
audio.c: In function ‘cdfs_make_header’:
audio.c:35: warning: implicit declaration of function ‘strcpy’
audio.c:35: warning: incompatible implicit declaration of built-in function ‘strcpy’
audio.c:36: warning: implicit declaration of function ‘cpu_to_le32’
audio.c:45: warning: implicit declaration of function ‘cpu_to_le16’
audio.c: At top level:
audio.c:61: warning: ‘struct super_block’ declared inside parameter list
audio.c: In function ‘cdfs_copy_from_cd’:
audio.c:64: error: storage size of ‘cdda’ isn’t known
audio.c:65: error: ‘CD_FRAMESIZE_RAW’ undeclared (first use in this function)
audio.c:65: error: (Each undeclared identifier is reported only once
audio.c:65: error: for each function it appears in.)
audio.c:66: error: dereferencing pointer to incomplete type
audio.c:67: error: ‘cd’ has no member named ‘track’
audio.c:76: error: ‘cd’ has no member named ‘cache’
audio.c:95: error: ‘CDROM_LBA’ undeclared (first use in this function)
audio.c:103: error: ‘cd’ has no member named ‘cache_sector’
audio.c:105: error: ‘cd’ has no member named ‘cache_sector’
audio.c:106: error: ‘CDROMREADAUDIO’ undeclared (first use in this function)
audio.c:106: warning: passing argument 1 of ‘cdfs_ioctl’ from incompatible pointer type
audio.c:108: warning: implicit declaration of function ‘printk’
audio.c:130: warning: implicit declaration of function ‘memcpy’
audio.c:130: warning: incompatible implicit declaration of built-in function ‘memcpy’
audio.c:64: warning: unused variable ‘cdda’
audio.c: At top level:
audio.c:138: error: expected declaration specifiers or ‘...’ before ‘size_t’
audio.c:138: warning: ‘struct inode’ declared inside parameter list
audio.c:138: error: conflicting types for ‘cdfs_cdda_file_read’
cdfs.h:140: error: previous declaration of ‘cdfs_cdda_file_read’ was here
audio.c: In function ‘cdfs_cdda_file_read’:
audio.c:139: error: ‘count’ undeclared (first use in this function)
audio.c:145: error: too many arguments to function ‘cdfs_cdda_file_read’
audio.c:146: error: too many arguments to function ‘cdfs_cdda_file_read’
audio.c:149: error: dereferencing pointer to incomplete type
audio.c:150: warning: incompatible implicit declaration of built-in function ‘memcpy’
audio.c:155: error: dereferencing pointer to incomplete type
audio.c:155: error: dereferencing pointer to incomplete type
audio.c: At top level:
audio.c:161: error: variable ‘cdfs_cdda_file_operations’ has initializer but incomplete type
audio.c:162: error: unknown field ‘read’ specified in initializer
audio.c:162: error: ‘generic_file_read’ undeclared here (not in a function)
audio.c:162: warning: excess elements in struct initializer
audio.c:162: warning: (near initialization for ‘cdfs_cdda_file_operations’)
audio.c:163: error: unknown field ‘mmap’ specified in initializer
audio.c:163: error: ‘generic_file_mmap’ undeclared here (not in a function)
audio.c:164: warning: excess elements in struct initializer
audio.c:164: warning: (near initialization for ‘cdfs_cdda_file_operations’)
audio.c:166: warning: ‘struct page’ declared inside parameter list
audio.c:166: warning: ‘struct file’ declared inside parameter list
audio.c:166: error: conflicting types for ‘kcdfsd_add_cdda_request’
cdfs.h:144: error: previous declaration of ‘kcdfsd_add_cdda_request’ was here
audio.c: In function ‘kcdfsd_add_cdda_request’:
audio.c:168: error: dereferencing pointer to incomplete type
audio.c:168: warning: passing argument 2 of ‘kcdfsd_add_request’ from incompatible pointer type
audio.c: At top level:
audio.c:171: error: variable ‘cdfs_cdda_aops’ has initializer but incomplete type
audio.c:172: error: unknown field ‘readpage’ specified in initializer
audio.c:173: warning: excess elements in struct initializer
audio.c:173: warning: (near initialization for ‘cdfs_cdda_aops’)
make: *** [audio.o] Error 1
What should I do now?

---

### Post by trent dillman on 2007-07-25
...

---

### Post by John Macnab on 2007-07-25
Oh goodness*really embarrassed here* I should think not, for I am such a dumb newbie that I dont even know what build essentials and kernel sources/headers are! Could I get some help if it wouldnt be too much to ask please?

---

### Post by trent dillman on 2007-07-25
...

---

### Post by John Macnab on 2007-07-25
Great! Tyvm indeed. I'll d/l them and see if it works.I'll get back but I've got a very slow net so would take me ages to d/l the stuff.Hopefully it'll work :) Thanks again

---

### Post by trent dillman on 2007-07-25
...

---

### Post by John Macnab on 2007-07-25
Hi
Well sir, I installed build-essential, linux-headers-generic 2.6.20-15.27,and linux-source2.6.20. But unfortunately the error is still occuring :( I guess maybe some other files are missing or something?I guess it would be hard to tell without looking into my puter?

---

### Post by John Macnab on 2007-07-27
Should I repost the errors again?*it takes too much space doesnt it*It looks like the same error everytime,even after reinstalling Ubuntu

---

### Post by John Macnab on 2007-07-28
Sorry to have troubled you all but I have finally got CDFS working.My VCD is mounting alright but I cant get it to play yet.Thanks for the help :)

---

