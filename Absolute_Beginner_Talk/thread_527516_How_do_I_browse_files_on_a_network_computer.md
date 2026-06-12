---
title: "How do I browse files on a network computer"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by j_ririe20 on 2007-08-16
I have Xubuntu and I am trying to open some files on a ubuntu server that was set up at my work. How can I do this?

---

### Post by bodhi.zazen on 2007-08-16
do you know if the server is using nfs, samba, ftp, or http ?

---

### Post by j_ririe20 on 2007-08-16
Yeah, the server is using samba

---

### Post by bodhi.zazen on 2007-08-16
See if these links help you :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

Also, if you are going linux -> linux nfs is very easy :)

[http://doc.gwos.org/index.php/NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

---

### Post by digeratess on 2007-08-16
> **bodhi.zazen said:**
> See if these links help you :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

Also, if you are going linux -> linux nfs is very easy :)

[http://doc.gwos.org/index.php/NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

I followed the easy way guide, but I still get Permission Denied when I try to edit files exported as RW from the server. Isn't there any configuration of user permissions required and if so, where is that done? What do you do about users that exist on the client machine but not on the server?

---

### Post by bodhi.zazen on 2007-08-17
Once the nfs share is mounted permissions are managed on the guest via chomd.

so say we mount a nfs share at /media/nfs

chown user.group /media/nfs

chmod xxx /media/nfs

nfs is not mounted per user. You can give users access by making a group nfs and these commands :

sudo chown root.nfs /media/nfs
sudo chmod 770 /media/nfs

HTH

---

### Post by ugm6hr on 2007-08-17
> **j_ririe20 said:**
> Yeah, the server is using samba

For Xubuntu / Windows shares (samba) - try the link in my signature to see how to use pyNeighborhood with Xubuntu.

---

