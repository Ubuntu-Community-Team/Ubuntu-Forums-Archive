---
title: "sharing folders between ubuntu users"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by notinamillionyears on 2005-10-15
hi there!
I've found stuff about using samba to share folders and files with ms windows, but didn't get how to simple share stuff on one machine with ubuntu onkly and between users... anybody could tell me how to do or show me the way (links and all)?
I'm pretty sure it's really easy and seems like a dumb question but I didn't figure it out, so helop welcome :)

thanx anyways

cy

---

### Post by GTvulse on 2005-10-15
NFS is the way to share directories with other Linux/Unix machines... You need to install the NFSv4 userland tools and server  (search nfs-common and nfs-kernel-server in Synaptic) and after that you can use the graphical administration tool in System->Administration->Shared Folders

---

### Post by LHZ on 2005-10-15
If you want to share files on the same filesystem between users, the key is setting you file permissions correctly.

By default, other users can ** read** the files in your home directory, but not **write** to them. If you want to share files, you can either change the file permissions of the files in your home directory, or you can make a new directory put the files in there, and then change the permissions. To change permissions you have two options:

1) Start Applications->System Tools->Filebrowser
    Find the files you want to share.
    Right click->Properties
    On the 'Permissions' tab, check all read/write/execute boxes.
    Apply

2) Start a command line, and type:
> 
chmod ugo+rwx <filename>

For example: 
> chmod ugo+rwx /wallpapers/ubuntu.bmp

After either of these methods, all users should be able to read and write to the file.

Keep in mind the following:

Both these methods open the file to everyone. If you want to open the file to some users, but not all , or give different users diferent forms of access, you'll need to use groups. Let me know if that's the case.

Only the file owner or root can change the file permissions. if you want to change the owner of a file, type
> 
sudo chown <username> <filename>

this can only be done by root (hence the 'sudo'). If you want a file browser wih root priviledges, type 
> 
gksudo nautilus


---

