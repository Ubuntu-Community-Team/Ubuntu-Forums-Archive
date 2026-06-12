---
title: "Identify Filesystem via ssh"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Jense on 2007-12-12
Hi,

I want to setup a network drive using the fstab to mount it permanently. I have a working server an can access it via the terminal using ssh. To mount it properly I need to name the filesystem in fstab (I think). So, how can I find out which file system the server is currently using.
The Network (or server) supports smb but I would like to use NFS since both mashines run linux.

Thx

---

### Post by Jense on 2007-12-12
nobody?

---

### Post by HermanAB on 2007-12-12
The command 'df' or 'mount' will show you what the real filesystems are.  However, NFS and Samba hides all that.  So when you do a network mount, the file system is 'nfs' for NFS and 'cifs' for Samba.

Cheers,

Herman

---

### Post by ShavenBaby on 2007-12-12
Just run df -hT at the terminal. This will give you details of the filesystems in use, size, type etc.

---

### Post by steync4 on 2007-12-12
Do you want to mount the server's data on another machine at boot?
Then you would need to mount the nfs or smb share like:
server:/usr/local/pub    /pub   nfs    rsize=8192,wsize=8192,timeo=14,intr

in fstab
if i remember correctly you can also include usernames/passwords here in the options

---

### Post by Jense on 2007-12-12
Thanks everybody for the help, I will check it out right away

cheers

Jens

---

### Post by The Cog on 2007-12-12
I found this article with google. I think it's what you're looking for:
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)
Here's the list of articles I found:
[http://www.google.co.uk/search?q=linux+mount+ssh](http://www.google.co.uk/search?q=linux+mount+ssh)

---

