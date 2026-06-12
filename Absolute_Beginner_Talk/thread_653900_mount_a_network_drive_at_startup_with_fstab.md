---
title: "mount a network drive at startup with fstab"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by asteinmetz on 2007-12-30
There are many threads on this subject and the method seems simple but something isn't working in my case.  I have NAS that exports an NFS share.  I can mount it manually but it is ignored in fstab.

This works (sudo does ask me for my pw before executing the command):
> 
$ sudo mount 192.168.2.254:/raid0/data/music Music


and then the mount command shows this (last line only)
> 
$ mount
192.168.2.254:/raid0/data/music on /home/art/Music type nfs (rw,addr=192.168.2.254)


and everything works fine.  Then I edit fstab to include this line

> 
//192.168.2.254:/raid0/data/music /home/art/Music auto    rw,user,noauto,exec 0       0


but the drive does not get mounted on startup.  Am I missing something? Thanks.

---

### Post by eternicode on 2007-12-30
```
**//**192.168.2.254:/raid0/data/music   /home/art/Music   **auto**   rw,user,noauto,exec   0   0
```

1) "type" of "auto"?  "auto" tells it to guess the FS.  Far as I can tell, you know it's an NFS share.  Try using "nfs" instead.

[https://www.virtualizationhero.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-nfs-client-config.html](https://www.virtualizationhero.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-nfs-client-config.html)

First google result for "fstab nfs"

2) remove the beginning "//" for the device.  That tells linux to look for a machine by that name in the local LAN.

You can test the fstab entry without rebooting by using
```
mount /home/art/Music
```
If you get an error of some sort, post it and your new fstab line.

EDIT:
By the looks of the IP address, this is a local machine.  Since it mounts fine with
```
$ sudo mount 192.168.2.254:/raid0/data/music Music
```
Try removing the "//" anyway.

---

### Post by Dilligaf on 2007-12-30
Try 

//192.168.2.254:/raid0/data/music /home/art/Music cifs rw,user,noauto,exec 0 0


run sudo mount -a in terminal and see what errors you get

Mike

---

### Post by eternicode on 2007-12-30
```
//192.168.2.254:/raid0/data/music /home/art/Music cifs rw,user,noauto,exec 0 0
```

What's "cifs"?  There's no man page for it, and it's not mentioned in the list of recognized filesystems in fstab's man page.

---

### Post by Dilligaf on 2007-12-30
cifs is the replacement for smbfs, they're both part of samba. Cifs has better support for large files. I didn't notice that the original poster had stated that the drive was nfs. Anyways running mount -a will give you an idea of whatis going wrong.

Mike

---

### Post by asteinmetz on 2007-12-30
Thanks guys! I think I have it.

I deleted the //, changed the "auto" to "nfs"  and removed the "noauto" switch.

This is the line in fstab now:
> 
192.168.2.254:/raid0/data/music /home/art/Music nfs    rw,user,exec 0       0


For the sake of future viewers I might as well mention another issue I had previously and solved on my own.  The default install of Ubuntu does not include the nfs server but mount doesn't complain if you try to mount an NFS share. I assumed to read an nfs share on another computer (thecus 1u4500 NAS) I didn't have to install the nfs server on the ubuntu client, but I did.  

> sudo apt-get install nfs-kernel-server

did the trick for me.  I figured this out by comparing the init.d files in two different ubuntu 7.10 vmware appliances available at the vmware site.  One appliance could mount the nfs share and the other couldn't.

---

### Post by gmalac on 2008-01-01
Hi,

Thanks for all this information, very useful.

I am trying to connect a remote PC (Ubuntu Linux, ext3 filesytem) in my home network.
On that PC I have shared a directory that I'd like to mount in my usual box (also Ubuntu Linux with ext3)

The line in fstab is as explained in this thread:
192.168.1.39:/home/guy/images /home/guy/ nfs rw,users,exec 0 0

sudo mount -a gives (after a couple of seconds):
mount.nfs: 192.168.1.39:/home/guy/images failed, reason given by server : permission denied

I have no problem accessing the directory thru Nautilus though

Am I missing something?

Thanks for any help

---

### Post by gmalac on 2008-01-02
Solved!

Actually I was missing all the server part very well documented here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server)

Hope this can help

Thanks!

---

