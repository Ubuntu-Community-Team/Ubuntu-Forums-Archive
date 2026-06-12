---
title: "help with ftpd"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-08-17
umm... i typed "sudo apt-get install ftpd" just so yall know what im workin with. i was able to connect useing a username and pass i already had. i made a new account called guest. the only problem is i can still access folders above it. how do i limit it to only guests home folder? and how do i edit it so that people cant delete things from that folder or upload things to it? and how would i make an anonymous login? oh... and i can only access my pc from a shell atm.

---

### Post by rmrf on 2005-08-17
I would recommend installing vsftpd from my experiences with how easy it is to configure.

> 
type:
sudo apt-get install vsftpd

NOTE: installing vsftpd will automatically remove and conflicting software, including ftpd.

type:
sudo gedit /etc/vsftpd.conf

search for this line:
#chroot_local_user=YES

delete the '#' sign

NOTE: when vsftpd is installed, it is automatically started, we need to restart it.

type:
sudo /etc/init.d/vsftpd restart

NOTE: this should restart the service, and when you log in, each user will be chrooted to their home directory.


hope this helps :cool:

EDIT: changed from vi to gedit to make instructions more user friendly. :)

---

