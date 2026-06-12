---
title: "problems with root privileges"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by Borack on 2008-11-06
Hi all!

I installed the ubuntu server 8.04 on my apple powermac g4. everything worked fine till yesterday. 

I want to use the ubuntur server for downloading torrents, start them remotely with ssh- which did already work fine. 

i have the bittornado package installed and use btdownloadcurses for the downloads. 

but since yesterday the files created after 'btdownloadcurses 'webadress-to-torrent-file' ' are owned by root. and after a short time btdownloadcurses shows status: download failed. 
then i get the error message: Couldn't allocate dir - [Errno 13] Permission denied: path/to/file

When i check the newly created folders, then i see that they are owned by the root and i have only read access. 

i already did some downloads and there the files/folders are owned by myself . 

so i did probably something dumb in the meantime ? .. but i don't think that i did something special .. or at least i can't rember  


Does anyone know what causes this problem ? 


Cheers
- Borack

( i did already ask the same question in the Absolute Beginner Talk forum some hours before: [http://ubuntuforums.org/showthread.php?t=972854](http://ubuntuforums.org/showthread.php?t=972854) )

---

### Post by cyberdork33 on 2008-11-06
Well, the two obvious ones...

1. make sure you are not running your client with sudo
2. make sure you are ssh'ing as the user and not as root.

---

### Post by Borack on 2008-11-06
Yes. Both with my own account

no sudo, or root. 

but now i've seen that the problem may be that i try to download the files directly on my mounted time capsule. might there be the problem?

---

### Post by cyberdork33 on 2008-11-06
OK well I am going to take a wild guess that it is likely a permissions issue related to how the Time Capsule is being mounted. Are you downloading items to the Time Capsule and then trying to access them from another machine / OS?

Have you tried accessing the files on the Time Capsule from the "server"? Does it allow your normal user access and modification privs?

---

### Post by Borack on 2008-11-06
> **cyberdork33 said:**
> OK well I am going to take a wild guess that it is likely a permissions issue related to how the Time Capsule is being mounted. Are you downloading items to the Time Capsule and then trying to access them from another machine / OS?


Yes, exactly. 

> **cyberdork33 said:**
> 
Have you tried accessing the files on the Time Capsule from the "server"? Does it allow your normal user access and modification privs?

If i access the server through ssh, navigate to the mounted time capsule and create a file e.g. touch test.txt -- well then the file is also under root privileges. hmm, not good. 

has it something to do how i mount the device?

mount.cifs //192.168.0.100/"Time Capsule"/ /media/capsule

this have i to do with sudo, otherwise it gives me a mount error: permission denied or not superuser and mount.cifs not installed SUID

---

### Post by Borack on 2008-11-06
mount.cifs //192.168.0.100/"Time Capsule"/ /media/capsule -o pass=password


sorry .. this is actually the way i mount the time capsule.

---

### Post by cyberdork33 on 2008-11-07
try this:
```
sudo mount.cifs //192.168.0.100/"Time Capsule"/ /media/capsule -o pass=password,file_mode=0777,dir_mode=0777
```If that works for you, then you can add a line to /etc/fstab to have it mount automatically every boot:
```
//192.168.0.100/"Time Capsule" /media/capsule cifs password=password,file_mode=0777,dir_mode=0777 0 0
```You can also put your password in a root-owned, hidden file if you don't want your pw to be so accessible and use the credentials option in fstab.

There is a lot of good info here:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by Borack on 2008-11-07
i tried it with the new mount options. 
but still the same. if i am on the time capsule. i can touch files manually ( as normal user , no sudo ) . but when i check the privileges with ls -al then it shows up that they are owned by root. the rights are set to -rw-r--r--.

---

### Post by cyberdork33 on 2008-11-07
If you mount the share with the "file_mode=0777,dir_mode=0777" options it your local user should see all files and directories on the share as rwxrwxrwx even though the Time Capsule actually stores the files on its hard drive differently.

---

### Post by Borack on 2008-11-07
well yes, 

i see the already existing files ( created not through ssh, but connection via os x ) as fully accesible, but the ones i create through ssh are only readable. 

```
drwxrwxrwx 1 root root 0 2008-11-07 20:18 music
-rw-r--r-- 1 root root 0 2008-11-07 20:19 test.txt
```

---

