---
title: "read write access with samba"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by chymo on 2006-08-20
I've been working with ubuntu for a month, installed lamp, and some other stuff all thanks to the posts on this forum which has been very helpful.  

I have ubuntu installed on a drive that also has a windows partition.  This windows partition has media files I'd like to access accross the lan.  So far I am able to read all the drives installed on this ubuntu/windows box from any other windows machine in my lan.  

Question - when accessing the files from other computers, how do I allow write access? Currently the ntfs partitions are read only.  I was playing around in smb.conf and /etc/fstab.  I changes some permissions in smb.conf to 755 or 777 and all in /etc/fstab was default (which should be rw access)  

Thanks for any help!

---

### Post by Kilz on 2006-08-20
> **chymo said:**
> I've been working with ubuntu for a month, installed lamp, and some other stuff all thanks to the posts on this forum which has been very helpful.  

I have ubuntu installed on a drive that also has a windows partition.  This windows partition has media files I'd like to access accross the lan.  So far I am able to read all the drives installed on this ubuntu/windows box from any other windows machine in my lan.  

Question - when accessing the files from other computers, how do I allow write access? Currently the ntfs partitions are read only.  I was playing around in smb.conf and /etc/fstab.  I changes some permissions in smb.conf to 755 or 777 and all in /etc/fstab was default (which should be rw access)  

Thanks for any help!
Writing to a ntfs partition from Linux isn't recommended. Someone is bound to tell you of some experimental new way of writing to a ntfs partition, don't do it unless you don't mind losing the contents of the drive if it corrupt. Experimental in this case is like "I just made some experimental brake pads from Swiss cheese. Why wants to drive 90 on the expressway with me?" experimental.

---

### Post by chymo on 2006-08-20
Really?!  Let me rehash this...  So you're saying I can't create, edit, save, delete files on an ntfs partition that are being served from drives in my linux box across the lan to a different windows machine?  So samba allows you to rw linux files via a windows box?  I do not want to risk the chance of corruption .  Is there a way I can set up an ftp server or something? Or, can I convert the ntfs partitions to become read/write regardless of when I'm booted up under ubuntu or windows?

---

### Post by BoneKracker on 2006-08-21
create a partition for your media files with a FAT filesystem on it
both unix and windows can read/write safely to FAT

you can do this from either windows or ubuntu

---

### Post by SonicSteve on 2006-10-12
I think some clarification is needed here. 
Writing to an NTFS partition that is on a "local" partition of a linux machine is experimental. 
HOWEVER...
It is perfectly safe to write to an NTFS partition over a network. It's safe because SAMBA is accessing it and Windows is actually doing the writing not Linux.
Having said that setting up write permission is something I'm still trying to figure out. 
By default the only user who will have write permission to any samba share is the Root user. Since you are likely not logged in as root (though this is tempting sometimes) you will only be able to read the share not write. 

Read this.it's a great how to.
[http://www.ubuntuforums.org/showthread.php?t=255872&highlight=samba+mount+permanent](http://www.ubuntuforums.org/showthread.php?t=255872&highlight=samba+mount+permanent)

---

### Post by Concolor on 2007-12-25
Bit o thread-rez here, but since google dumped me here, I might be able to help others.

*ahem* Those wiser than me have come up with something that helped me greatly. Only thing I had to change was file type from "cifs" to "smbfs".

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/]("http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/")

---

