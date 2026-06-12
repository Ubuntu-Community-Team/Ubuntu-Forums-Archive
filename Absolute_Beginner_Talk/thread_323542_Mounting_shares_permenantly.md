---
title: "Mounting shares permenantly"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-22
How does one mount the smaba shares and NFS Shares permenantly ??

---

### Post by dannyboy79 on 2006-12-22
> **lance_klusener said:**
> How does one mount the smaba shares and NFS Shares permenantly ??

this is for smbfs, check it out: works great: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by lance_klusener on 2006-12-22
Thanks , so i need to add the line 
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0


in the /etc/fstab file

---

### Post by dannyboy79 on 2006-12-22
> **lance_klusener said:**
> Thanks , so i need to add the line 
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0


in the /etc/fstab file

i would use a credentials file but yes. also, I have read that smbfs is on the outs and cifs is going to be replacing it. maybe do a gogle search on mount using cifs. also, don't forget to install smbfs and all it's dependencies.

---

### Post by lance_klusener on 2006-12-22
Yes smbfs is installed ( it is working on ubuntu which tells me that i dont need to install anything more , is that the case ??? )

---

### Post by dannyboy79 on 2006-12-22
> **lance_klusener said:**
> Yes smbfs is installed ( it is working on ubuntu which tells me that i dont need to install anything more , is that the case ??? )

well if it's working than you're good to go. it's up to you whether or not you want to look into using cifs. i heard that's it's better than smbfs as well as going to be the standard soon.

---

