---
title: "Sharing Files"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-03-30
I tried to share a folder. However, when I access it on Windows XP, I get a prompt for a username and password. I am not sure what to enter here. I tried entering my Ubuntu username and password, but that did not work. How can I access shared folders on my Windows XP system? Thanks!

---

### Post by rado_london on 2006-03-30
Same problem here. People please help us.
I have some idas, probably it is the samba username or something like that but still need help for changing it etc.

---

### Post by patrick295767 on 2006-03-30
[QUOTE=amitroy5]I tried to share a folder. However, when I access it on Windows XP, I get a prompt for a username and password. I am not sure what to enter here. I tried entering my Ubuntu username and password, but that did not work. How can I access shared folders on my Windows XP system? Thanks![/QUOTE]
  
U mean that a folder from the Windows XP system will be shared ?  
or one folder of the Ubuntu ?
  Mounting the Share
----------------------
To mount an smbfs share from a Linux workstation at the command line, you can use either the smbmount command or use mount -t smbfs. Both command will work the same. When you use mount -t smbfs, the mount program actually passes the command over to smbmount for execution. Throughout this document I'll use smbmount instead of mount -t smbfs. 
An example would look like this: 
```
smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```
The mount equivelant is: 
```
mount -t smbfs //servername/sharename /mountdirectory -o 
```username=mywindowsusername,password=mywindowspassword
//servername/sharename refers to the name of the Windows computer and the name of the share. 
/mountdirectory refers to the directory you use as the mount point on the Linux workstation. It can be any directory as long as the user executing the command has rights to it. 
Whether you need to supply a username and password depends on what type of security you have on the Windows share. If you have a share created with no password on it, you shouldn't need to provide a username and password. If the share happens to be on a Windows NT server that is part of a domain, you would need to provide a domain login name and password.

---

