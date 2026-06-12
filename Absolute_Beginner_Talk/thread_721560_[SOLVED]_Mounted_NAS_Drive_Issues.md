---
title: "[SOLVED] Mounted NAS Drive Issues"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-03-11
I am using the following line in /etc/fstab to mount my NAS drive so that programs that are unable to browse the network are able to see it:
```
//192.168.0.XX/bigdisk /home/myuser/BigDisk cifs auto,uid=myuser,gid=myuser,defaults,username=XXXXX,password=XXXXX,d_mode=0777,file_mode=0777
```
but when I restart I get a lot of Network Manager errors due to the fact that it is still mounted. Is there an entry I can make that will auto-unmount on restart/shutdown? I know I can umount before restarting/shutting down but would like to have it take care of itself if possible. 

Also, my NAS drive will periodically make a bunch of noise (as if I am doing a properties check on it) though no changes have been made and I have not tried to access it. Is there a way to keep this from happening?

Edit: I moved the mount directory from my /home/myuser to my / directory and that solved the problem with random noise coming from the drive. I put it in / rather than in mnt or media because I do not want a desktop icon.

---

### Post by candtalan on 2008-03-11
I found this thread most useful:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

fwiw CIFS might be one of the issues maybe?
good luck

---

### Post by DamonChyld on 2008-03-12
Thanks for the link candtalan, it brought my attention to the vulnerability of having user/pass in fstab. I followed the thread but still have the NetworkManager errors on restart/shutdown if I do not umount the drive first though. Any other advice?

---

### Post by Iowan on 2008-03-12
I don't have the necessary details, but an entry in the** rc0.d** directory to  unmount the  NAS should help.

---

### Post by DamonChyld on 2008-03-13
Thanks for pointing me in the right direction Iowan. I was able to fix my problem my running the following commands as root
```
ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```
(from [http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/](http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/))

A google search also pulled up a thread on these forums ([http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)) where they are recommending using one of a few scripts they wrote for this purpose. I do not know what the advantage of using these scripts over the /etc/init.d/umountnfs.sh script already present in ubuntu is, but perhaps this can help someone as well.

---

