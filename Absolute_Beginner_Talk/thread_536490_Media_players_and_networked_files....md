---
title: "Media players and networked files..."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by PsycoGeek on 2007-08-27
I have been able to gain access to my Windows2k server where I have all of my personal files, and media files (music mostly).   I have "mapped" a connection to the files, with a link on my desktop and can get to them (browse and play the files and use the playlists I have stored there in m3u format) with Rhythmbox, but can't see the network connection in other players such as Exaile and XMMS.  I can't scan the network locations into the libraries...

Can anyone tell me how to get to the network location with any other media player?

---

### Post by KCPokes on 2007-08-27
Try mounting your drives using smbfs.  The following link should help:

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by PsycoGeek on 2007-08-28
I take it the "Connect to Server" under "Places" on the bar next to "Applications" is not the same as mounting in the link you provided?

Thanks for the reply, BTW.  I appreciate it.

---

### Post by PsycoGeek on 2007-08-28
OK, when I try that:

smbmount //server1/music /home/daled -o username=daled,password=mypassword

... I get:

smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

What am I doing wrong?

---

### Post by PsycoGeek on 2007-08-29
Anyone?  

If I can get around this problem and get other music players besides Rhythmbox Ubuntu is going on all of my PC's in dual-boot setups, at least until I get the games we play running under Wine.  One step at a time though... need to get this solved first.

---

### Post by quantumcheese on 2007-08-29
I don't know samba, but the error message looks like putting "sudo" in front of your command would help.  (sudo = do as super-user (root))

---

### Post by PsycoGeek on 2007-08-29
Thanks.  I also just found this thread:

[http://ubuntuforums.org/showthread.php?t=537823]("http://http://ubuntuforums.org/showthread.php?t=537823")

in which was this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read")

which is getting me where I want to be with this.  Now mabe I can try some of the other distro's again with better success.

One step at a time...  one step closer to freedom! 

Thanks to all who helped.

---

