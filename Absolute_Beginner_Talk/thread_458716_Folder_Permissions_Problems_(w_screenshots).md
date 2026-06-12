---
title: "Folder Permissions Problems (w/ screenshots)"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by actionaction on 2007-05-29
I just recently set up several samba shares over my network (one internal 120 gb hd, one internal 500 gb hd, and one 500 gb external (USB) hd). the external usb 500 gb hd is called "usbdisk" and is mounted as such. the internal 500 gb hd is called "storage" and is mounted at /media/storage. the 120 gb and the 500 gb external (usbdisk) i have not had any problems with. The internal 500 gb hd i have had problems with however, permissions wise. For some reason it will not let me change permissions, by using both GUI and terminal. i get an error in terminal whenever i perform the command
```
sudo chown -R michaelzincone:michaelzincone /media/storage
sudo chmod -R 755 /media/storage
```

and when i view the permissions of it, i get this
[IMG]http://img45.imageshack.us/img45/9305/storage500problempropropg3.png[/IMG]

I am running Ubuntu 6.06 (Dapper Drake)
Thanks alot!

---

### Post by smylie on 2007-05-30
Two things to check
1) The permissions on the local folder (ie before the samba share is mounted)
2) The permissions given to the samba share on the samba server (/etc/samba/smb.conf)

Also, to save the hassle of screenshots in future, you can use ls. ie
```
$ ls -l /media/
```

Cheers
Dave Smylie

---

### Post by actionaction on 2007-05-30
i showed the permissions above, and it won't let me change them. any ideas?

---

