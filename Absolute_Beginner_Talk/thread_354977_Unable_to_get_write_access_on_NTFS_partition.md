---
title: "Unable to get write access on NTFS partition"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2007-02-06
I followed about four different tutorials on mounting and getting write access on my Windows NTFS partion, but none of them worked correctly. Any help would be appreciated. I'm going to try to give as much info as possible. I'm using Ubuntu 6.06.

I have the partition mounted successfully (I think) to /media/windows. I can read the directory and write a new file using the sudo commands from the terminal, but when I try to access it on the File Browser it says "You do not have the permissions necessary to view the contents of 'windows'."

I mounted it using "sudo mount /dev/hda1 /media/windows" I also tried using "sudo ntfsmount /dev/hda1 /meda/windows -o force" Both mount it fine, but I can't get write access.

The line i have in my /etc/fstab file reads "/dev/hda1 	/media/windows	ntfs 	rw,user,group=ntfs 	0 	0"

I added myself to the NTFS group. If I type in umask on the terminal it reports "0022".

I tried messing around with the fstab file for about 2 hours last night, but nothing I put would make it work. Any ideas?

---

### Post by meng on 2007-02-06
Yep, you've overlooked the fact that ntfs on linux is read-only access. There is read-write access available, using ntfs-3g, but note that this is considered by some to be experimental (so don't come crying if/when you lose all your data), although most users reckon it's safe.

Search the forums for a howto on ntfs-3g.

---

### Post by kebes on 2007-02-06
This entry in the unofficial Ubuntu Guide explains what to do:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

As meng said, you need to install ntfs-3g if you want to be able to write to NTFS drives. Adding this support is easy, but again, be aware that NTFS-write is not yet considered to be 100% reliable.

---

### Post by TekMuzik on 2007-02-06
> **meng said:**
> Yep, you've overlooked the fact that ntfs on linux is read-only access. There is read-write access available, using ntfs-3g, but note that this is considered by some to be experimental (so don't come crying if/when you lose all your data), although most users reckon it's safe.

Search the forums for a howto on ntfs-3g.

But most of the guides say "Note that Ubuntu will read but not write to NTFS formatted drives unless the fuse tools are installed." I installed the fuse tools. And not even concerning write access, my File Browser won't even display the files, so I assume it's not even giving me read access.

---

### Post by TekMuzik on 2007-02-06
> **kebes said:**
> This entry in the unofficial Ubuntu Guide explains what to do:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

As meng said, you need to install ntfs-3g if you want to be able to write to NTFS drives. Adding this support is easy, but again, be aware that NTFS-write is not yet considered to be 100% reliable.

I'll try that guide, and let you know how it goes. Thanks.

---

### Post by carverj on 2007-02-06
Also, a handy little program. Very quick and easy

[http://linux.softpedia.com/get/System/Hardware/Ntfs-config-22435.shtml](http://linux.softpedia.com/get/System/Hardware/Ntfs-config-22435.shtml)

Enjoy

---

### Post by TekMuzik on 2007-02-06
> **kebes said:**
> This entry in the unofficial Ubuntu Guide explains what to do:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

As meng said, you need to install ntfs-3g if you want to be able to write to NTFS drives. Adding this support is easy, but again, be aware that NTFS-write is not yet considered to be 100% reliable.

I keep getting "E: Couldn't find package ntfs-3g" even after enabling the repositories.

---

### Post by bodhi.zazen on 2007-02-06
Try this:

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

---

### Post by meng on 2007-02-06
> **TekMuzik said:**
> I keep getting "E: Couldn't find package ntfs-3g" even after enabling the repositories.
Are you running Edgy or Dapper? Because those instructions are for Edgy.

---

### Post by TekMuzik on 2007-02-06
> **bodhi.zazen said:**
> Try this:

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

GOT IT! Thank you so much!

---

