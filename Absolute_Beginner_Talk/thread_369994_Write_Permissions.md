---
title: "Write Permissions"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by brent_t on 2007-02-25
Anyone help me to change this write permissions?
/dev/hdb1 /media/0\040GB\040Disk\040(hdb1) ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

I would like to mount this on a networked share and use it with amarok but their instructions seem vague to a noob.

Thanks for any help, I am still learning the ways...

---

### Post by Mornedhel on 2007-02-25
*Write* permissions ? It's an NTFS drive, it's unlikely you want to write to it with Linux, unless you want to try experimental stuff (not necessarily wise). Anyway, you need to get writing support for NTFS before you change the permissions.

---

### Post by terdon on 2007-02-25
check out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by brent_t on 2007-02-25
thanks for the replies, I don't really need to write to it, but need to access it with amarok where I can add it to my collection. When it scans the collection the way I have it mounted, it screws up.
I tried using xsmbrowser. Didn't make any diff. Mounted it in /root/mnt/ect, ect.
Would like to stream music from a diff computer over my workgroup. Amork says it's they way I have it mounted, but I am too new to get it....

Thanks,
Brent

---

### Post by brent_t on 2007-02-27
I since changed the drive to ext3 and it still won't work., but I give. I should be asking aramok anyways....

---

