---
title: "mounting samba share permission problem"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by coxeh on 2007-05-26
Hi,

im having problems with permission problems when mounting a samba share to a drive.

i can create/delete folders and files, but i cannot alter the files, 

its not the share as i have full access on another windows box.

i have this in my fstab and it mounts ok
```

//192.168.0.*/path	/media/server	cifs	username=user,password=pass,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```

why cant i change files ??

Thanks 
Carl

---

### Post by coxeh on 2007-05-27
I have found the problem, look like i needed to add a  noperm option into my fstab

```

//192.168.0.*/path	/media/server	cifs	noperm,username=user,password=pass,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```

---

### Post by dave-5B on 2007-05-27
are you connecting between two *nix boxes? if so its much faster and easier to use sshfs (which uses the ssh / scp protocol to transfer files) 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29)

if your mounting a directory on a windows comp:

[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by bYOndo on 2007-08-08
> **coxeh said:**
> I have found the problem, look like i needed to add a  noperm option into my fstab

```

//192.168.0.*/path	/media/server	cifs	noperm,username=user,password=pass,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```

Great! the same problem here and "noperm" option has solved it! finally I can use my Lacie Ethernet Disk (and my headaches ended ;) )

thanks, 
Massimo

---

