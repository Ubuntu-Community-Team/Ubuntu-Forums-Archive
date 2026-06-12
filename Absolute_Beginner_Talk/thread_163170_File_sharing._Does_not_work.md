---
title: "File sharing. Does not work"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-04-20
I am trying to share files with other users on the same computer.  I read one of the other threads in this forum and did the fallowing:

sudo mkdir /share
sudo chmod 777 /share
ln -s /share/home/username

I now have a file named share in my home folder that is locked.  I cannot change permissions and I cannot delete or put anything into the folder.

any help?

---

### Post by jorn on 2006-04-20
Type in terminal:
gksudo nautilus
That's the root filemanager.
Go to the locked folder rightclick > properties>Permissions.
Maybe you can change permission there.

---

### Post by nsmith on 2006-04-20
Jorn,

That worked thanks :D

---

### Post by Jose Catre-Vandis on 2006-04-20
I tried this and it killed my installation (had to reinstall).

Is this the "best" way of changing the permissions for a folder in "/" ?

can you use a umask setting somewhere, like with mounts ?

---

### Post by nsmith on 2006-04-21
I´m still trying to figure out this file sharing.  I have a folder in my home folder named share.  I thought I would be sharing that folder but when I put folders into the share folder they are not shared.  Also if I have documents in my home folder they are shared but not other folders.

Maybe I need to clarify what I want to share.  I would like to share a folder called my music that is inside my home folder.  The folder contains many sub-folders and inside those folders more folders.  How can I share just this folder "my music" and all its contents/subcontents with another user on the same computer?

---

### Post by Jose Catre-Vandis on 2006-04-21
Have you got samba installed. This really helps!

```
sudo apt-get update
sudo apt-get install samba
sudo apt-get install smbfs
```

Then use System>Adminstration>Shared Folders

Check out wiki here:

[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)
or Unofficial Guidehere:
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by jorn on 2006-04-21
What happens if you rightclick it and choose share?

---

### Post by nsmith on 2006-04-21
> What happens if you rightclick it and choose share?

It does not share with other users on the same computer.  I am assuming that it shares on a network.

Also isnt samba for network shares?  I will try it anyway and I think I already did that but at this point I cant remember what all I have done.

---

### Post by skinnygmg on 2006-04-21
users would probably need access to your home folder for this to work the way you want.  try creating/moving your "my music" folder up a level (same as "user's home" folders).  then chmod 777 "filename".  use -R to open the permissions on the sub-directories/files.  you don't need to "share" it if the permissions are wide open.  you might need to sudo to create folders/change permissions at this level.  post back if this works.

---

### Post by Jose Catre-Vandis on 2006-04-21
[QUOTE=nsmith]It does not share with other users on the same computer.  I am assuming that it shares on a network.

Also isnt samba for network shares?  I will try it anyway and I think I already did that but at this point I cant remember what all I have done.[/QUOTE]

Sorry, wasn't concentrating!

---

