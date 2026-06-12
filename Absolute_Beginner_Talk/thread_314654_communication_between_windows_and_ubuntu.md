---
title: "communication between windows and ubuntu"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by bhavesh on 2006-12-07
Hello folks , 
             The following is the problem that i am trying to solve :

1] I have a windows xp machine , in which i have started ubuntu using VMWare.

2] The windows machine ( name of the machine : win-user ) has access to some of the shares ( e.g: //college/docs )

3] Now i want ubuntu to have access to the shares( //company/docs ) , this share is password protected too . I dont know how to accomplish this  task.

Please give your inputs .

Thanks in advance , 
Bhavesh.

---

### Post by lemonsCC on 2006-12-07
As these documents seem to be of utmost importance I **would not** try enabling write access to your xp partition.  The simplest way to share the files between both Ubuntu and XP is to create a FAT32 partition which everything can utilize.

---

### Post by bhavesh on 2006-12-07
The thing is that the "//college/docs" are on the network and are not present on the windows machine 

The windows machine has to mount the drive to acces those shares 

So in this situation how do i get ubuntu to access the shares.

Thanks for your reply , 
Bhavesh.

---

### Post by lemonsCC on 2006-12-07
Hmm do you happen to know what the format of the network drive is?  if it is ntfs (xp's default)  you are going to have a hard time.

---

### Post by dannyboy79 on 2006-12-07
if you only want access to the docs than it doesn't matter that the fs is ntfs, samba can access almost any fs! just mount the folder just like you'd mount a folder if it were on your windows box. do you have smbfs or cifs installed? I would do a few searchs within this forums about mounting windows shares (fat32 or ntfs) and you'll have you answer. actually I had this bookmarked, check this out: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html). good luck

---

### Post by bhavesh on 2006-12-07
Yes i think using the "smdfs" will solve the issue .

Thank you very much for your quick replies

---

### Post by lemonsCC on 2006-12-07
> **dannyboy79 said:**
> if you only want access to the docs than it doesn't matter that the fs is ntfs, samba can access almost any fs! just mount the folder just like you'd mount a folder if it were on your windows box. do you have smbfs or cifs installed? I would do a few searchs within this forums about mounting windows shares (fat32 or ntfs) and you'll have you answer. actually I had this bookmarked, check this out: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html). good luck

good point about read-only  i assumed read and write access.

---

### Post by bhavesh on 2006-12-08
Guys i tried mounting the drive "\\college\docs" , but it gave me a error saying that 

27097: Connection to college failed
SMB connection failed

"college" is the name of the windows machine.So i think that samba cannot find such a machine on the network 

But i know the IP adress of the machine college.

So is there any way to tell samba to load the share from a particular IP.

Thanks , 
Bhavesh

---

