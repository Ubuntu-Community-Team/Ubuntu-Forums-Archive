---
title: "Why does mount.cifs take a million times more time to mount than smbfs?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by descentspb on 2008-01-14
Subject in the name

---

### Post by descentspb on 2008-01-15
bump :)

---

### Post by cmittle on 2008-01-15
This is a vague question if you don't give us more information.  What command did you use that cifs took so long to mount?  What command did you use that made smbfs work so well?  I imagine you are mounting a drive from a file server?  When I do this I use
```
sudo mount -t cifs //192.168.***.***/homes -o username=**** /mount/directory
```
I was reading a server tutorial and they told me to use this command, I tried it and it worked so I stuck with it.  Maybe this will help, maybe not, but if you provide people with more information we should be able to help you answer your questions.
Maybe you don't have the most up to date version of the cifs module?  Try typing modinfo cifs in the command line and see what you get.  This is my result, and mounting with cifs happens in the blink of an eye.
```
modinfo cifs
filename:       /lib/modules/2.6.22-14-generic/kernel/fs/cifs/cifs.ko
version:        1.49
description:    VFS to access servers complying with the SNIA CIFS Specification e.g. Samba and Windows
license:        GPL
author:         Steve French <sfrench@us.ibm.com>
srcversion:     30616BA7D30E1F22CF9B850
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           CIFSMaxBufSize:Network buffer size (not including header). Default: 16384 Range: 8192 to 130048 (int)
parm:           cifs_min_rcv:Network buffers in pool. Default: 4 Range: 1 to 64 (int)
parm:           cifs_min_small:Small network buffers in pool. Default: 30 Range: 2 to 256 (int)
parm:           cifs_max_pending:Simultaneous requests to server. Default: 50 Range: 2 to 256 (int)
`
```

---

### Post by descentspb on 2008-01-15
Sure, i gladly will!

That's what modinfo cifs tells me:

> filename:       /lib/modules/2.6.22-14-generic/kernel/fs/cifs/cifs.ko
version:        1.49
description:    VFS to access servers complying with the SNIA CIFS Specification e.g. Samba and Windows
license:        GPL
author:         Steve French <sfrench@us.ibm.com>
srcversion:     30616BA7D30E1F22CF9B850
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           CIFSMaxBufSize:Network buffer size (not including header). Default: 16384 Range: 8192 to 130048 (int)
parm:           cifs_min_rcv:Network buffers in pool. Default: 4 Range: 1 to 64 (int)
parm:           cifs_min_small:Small network buffers in pool. Default: 30 Range: 2 to 256 (int)
parm:           cifs_max_pending:Simultaneous requests to server. Default: 50 Range: 2 to 256 (int)

i used both "mount.cifs" and "mount -t cifs"
for example the command is:
> sudo mount -t cifs //gopher-server/video /mnt/gopher

it takes several minutes to mount

but when trying to do it through "mount.smbfs" or "mount -t smbfs" it takes a couple of seconds.
> sudo mount -t smbfs //gopher-server/video /mnt/gopher

This happens not with all the resources on my network, but with many (i believe with the ones, which are not in my subnetwork)

Though when i try to mount my own smb shares mount.cifs works ok and fast.

---

### Post by descentspb on 2008-01-15
Well, i figured out the problem:
I should connect to port 139, not 445. I think it takes to long to scan port 445 when mounting cifs.
When i tried to mount smbfs it said it cannot conect to IP:445 and mounted the share succesfully!

I think now that the default port of 445 is the problem, why nautilus mounts smb so long. Is there a way to change the default connect port of mount.cifs, mount.smbfs and nautilus?

---

### Post by cmittle on 2008-01-16
I do not know anything about the default ports, so I can't help you there.  I'm not sure that I understand, you are mounting the network drive via nautilus?  Why not from the command line?

---

### Post by descentspb on 2008-01-16
it is pretty much easier to write
 "smb://slyer/HDTV"
 in nautilus than
"sudo mount -t cifs //slyer/HDTV /mnt/HDTV -o iocharset=utf8,codepage=cp866,port=139,guest"
 in command line. But the first one takes much more time to mount than the second, and i believe this is also because of the default port.

---

### Post by cmittle on 2008-01-16
You could enter that command in your /etc/fstab and mounting should be as simple as typing mount HDTV.

---

