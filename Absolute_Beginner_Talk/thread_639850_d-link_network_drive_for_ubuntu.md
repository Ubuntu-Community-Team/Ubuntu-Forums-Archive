---
title: "d-link network drive for ubuntu ???"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by lost4now on 2007-12-13
I have searched and dug around  but havent found any answers.

I have a D-link DNS-323 networ drive I would like to use as a backup storage location. All I can find is for windows. Does anyone know of or where I can get a how to or any other info on using the network drive with ubuntu.

Thanks

---

### Post by d0nny2600 on 2007-12-14
How does it connect in Windows? Directly to a hub I assume?
In which case the network drive will be assigned an IP. Try pinging it from Ubuntu. ping xx.xx.xx.xx 
If you get a response it should be easy to access through Linux. What filesystem is it formatted to?

---

### Post by lanemeyer67ss on 2008-02-25
i'm interested in this also.  i can't find an easy HOW-TO with this NAS, though it seems like there are a lot of people that have this.  i'm just looking to connect to it and store files.:confused:

---

### Post by Randulf on 2008-02-26
Hi!
Im using the DNS-323 together with ubuntu.

What you have to do is mount it. I mount it in my fstab file (/etc/fstab) using cifs. I have tried samba but get really slow speeds. 

This is the line I have added to fstab:
```
//192.168.1.xx/my_nas_dir /home/user/mount_point smbfs auto,username=xxx,password=xxx,uid=1000,gid=users,umask=000,user 0 0
```
switch smbfs to cifs if you want to use that instead.
After you added the line in fstab type:
sudo mount -a

---

