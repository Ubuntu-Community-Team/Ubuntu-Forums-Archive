---
title: "Linux Networking"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-08-08
Ok...I feel like an idiot...cause i feel like i should know this..,I installed Samba, and shared some folders...but how do i go about accessing those folders from another linux machine??? On both machines, I can go to the  Network Servers>windows Network>MSHOME And I can see both machines on that list (and yes, I have folders shared) but I see nothing when i open either one in the network..no shared folders...did I do something wrong?

---

### Post by Fondor1 on 2006-08-08
I'm having the same trouble, though admittedly I didn't look into it too much.  Instead I ended up just using ssh to transfer files between boxes on my network.

---

### Post by echo $USER on 2006-08-08
> **bladefallcon said:**
> Ok...I feel like an idiot...cause i feel like i should know this..,I installed Samba, and shared some folders...but how do i go about accessing those folders from another linux machine??? On both machines, I can go to the  Network Servers>windows Network>MSHOME And I can see both machines on that list (and yes, I have folders shared) but I see nothing when i open either one in the network..no shared folders...did I do something wrong?


If you netowrking linux boxes only, you should have a look at NFS.  Here is the how to...

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by patrickthebold on 2006-08-08
I'm not sure if you have to restart samba or not when you change the settings but try /etc/rc5.d/S20Samba restart.  Also look at smbpasswd.

---

