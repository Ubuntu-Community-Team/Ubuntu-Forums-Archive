---
title: "Unmounting file system(URGENT!!!)"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-06-01
Hi,

i have one critical suitation.. pls help 

i have mounted an ext3 partition (sda4)  on to my home directory /home/user01 in ubuntu (pity this is also ext3) (sda5). i have done some changes in that....


if suppose i unmount that does all the folder in my home dir goes away?


this is the normal umount command i suppose:

> 
umount /home/user01

 or is it possible to unmount the filesystem without affecting my home settings/files..


im waiting for reply so that i can give it now.

---

### Post by sandwitch on 2007-06-01
if you do a: "mount | grep sda4" You will find out where its mounted, then do "umount <mountpoint here>" and your in business

---

### Post by sankarv on 2007-06-01
see i know the mount point where sda4 is mounted. its mounted in /home/user01 since i only have mounted this before. 


The command u gave this command gives output

*/dev/sda4  on /home/ms199932 type ext3*



something like this.


my problem/question is, if i give unmount, also the files which were present in my home directory originally before mounting sda4 there will also go away?

---

### Post by sandwitch on 2007-06-01
sorry 
they will be there :)

---

### Post by rillip on 2007-06-01
The files are not removed, however, you will not be able to access them until you mount sda4 again, there or somewhere else.

---

