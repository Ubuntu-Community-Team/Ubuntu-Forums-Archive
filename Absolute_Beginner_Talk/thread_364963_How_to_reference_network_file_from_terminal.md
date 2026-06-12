---
title: "How to reference network file from terminal"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by mnb on 2007-02-18
Hi All,

I've got Edgy Eft up and mostly working with my home LAN to a couple of XP machines.  I can browse the LAN fine with the graphical browser... but I'm stumped on how to reference a file across the network from a terminal (as a command line option).

I've tried some strings similar to cat "smb://rigel/documents and settings/mike/my documents/file.txt", etc. but I've been unable to get the correct reference syntax down - can someone please give me some pointers?

Thanks,

mnb

---

### Post by raja on 2007-02-18
Hi,
I know that you can install smbfs (Samba filesystem) and then mount the samba share with ```
mount -t smbfs <samba share> <mount point>
```. I use this method to access a folder on my windows box from ubuntu running within vmware. But I am not sure if there may not be another way to do it.

---

### Post by kidders on 2007-02-18
Eep! Too slow!

[COLOR="Gray"]Hi there,

URIs that start with things like http://, smb://, etc. are application-dependent. You will find, for instance, that not all graphical applications support them ... and, as you've mentioned, a dumb terminal shell certainly won't.

The best way to make sure that your data (networked or not) is always accessible to every service/application is to mount it, which integrates it seamlessly into your basic filesystem structure. You may, for instance, be familiar with the idea of mounting USB disks at locations like /media/myusbdisk, or mounting a partition from another operating system into your home directory somewhere.

Mounting Samba, NFS & other shares works the same way (although some of the advanced mount options are a bit different). Samba provides a tool called **smbmount** that you might find useful, but there's no reason you can't add remote filesystems into your /etc/fstab and have them plugged into your local root filesystem automatically.

[LIST]
[*]Windows filesharing (Samba) paths are written like this: //server/sharename
[*]NFS shares are usually written as server:/path/to/share
[/LIST][/COLOR]

---

