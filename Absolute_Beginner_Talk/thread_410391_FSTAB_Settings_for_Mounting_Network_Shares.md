---
title: "FSTAB Settings for Mounting Network Shares"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-15
Let me see if I can explain this correctly, I am trying to wrap my mind around it, but I may still get part of it wrong....


I have 3 shared drives on my file server, which is running Ubuntu Server 6.10 and all 3 of these drives are mounted to folders which I have chmod'd to rwxrwxrwx for everyone to see/share/write.  When I browse to these shares from any other machine on my network, Linux or Windows, I can access them fine with read/write/execute or anything.

Now, from my other Ubuntu box, running 6.10 Edgy, as I said I can browse to the server shares through the "Network Servers" option in the Places menu and access them fine.  However, I tried mounting them to a folder on my local machine and I cannot seem to get the permissions correct.  When I mount them, I can either READ ONLY to the folders or I can't access them at all.

Each time I reboot I have to try and remount them again and deal with the permissions, chown, and all that.

The shares on my local machine are:
/mnt/shares/Wdrive
/mnt/shares/Ydrive
/mnt/shares/Zdrive

I am using this cmd below in order 
```
mount -t smbfs -o gid=jsamba,uid=jsamba //10.10.10.82/Zdrive /mnt/shares/Zdrive
```

And even though my login username is [COLOR="Blue"]jason [/COLOR]and this username IS in the [COLOR="Blue"]jsamba[/COLOR] group, I still cannot access this share except for READ ONLY.

So I guess my question is......... what command should I use to mount these COMPLETELY OPEN shares from the network to my local machine and what should I place in the FSTAB file so that when I reboot I don't have to do it all over again?

---

### Post by spin2cool on 2007-04-15
Have you looked here?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by kc5hwb on 2007-04-15
Although that is a different way of doing it from what I was expecting, that looks like it would work.  Thanks for that link.

---

### Post by kc5hwb on 2007-04-16
ok, I ran this update on this file, rebooted and it works fine.  However, when I run a ls -l command on the new folder that is mounted with the network share, it shows the uid and the gid both as root.

```
drwxrwxrwx 1 root root 4096 2007-04-16 17:13 Wdrive
```

Now I can access this folder fine (without using root) and I can create folders inside of this one fine also.  However, all the folders that already existed there, I can only READ ONLY.

Will I have to create all new folders?

---

