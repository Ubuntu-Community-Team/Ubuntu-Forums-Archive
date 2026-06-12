---
title: "Cant get NFS share to work ... help please."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by dan fisher on 2008-02-12
I have followed this url to set up an nfs share:

[https://help.ubuntu.com/7.10/server/C/network-file-system.html](https://help.ubuntu.com/7.10/server/C/network-file-system.html)

my exports file on the server machine reads:

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
/home/dan 192.168.0.3(rw,sync,no_root_squash)

192.168.0.3 is the inet address of wlan0 on the client which is shown using "ifconfig"

I restart the NFS server as instructed: "sudo /etc/init.d/nfs-kernel-server start"

Then on the client to try and mount the directory on the server I issue:

"sudo mount 192.168.0.2:/home/dan /home/dan"

192.168.0.2 is the inet address of wlan0 on the server.

In response to that the directory isn't mounted and I get the message:

mount: wrong fs type, bad option, bad superblock on 192.168.0.2:/home/dan, 
missing codepage or helper program, or other error  
In some cases useful info is found in syslog - try 
dmesg | tail or so

ANYONE PLEASE?

---

### Post by zvacet on 2008-02-12
Maybe [this](https://help.ubuntu.com/community/SettingUpNFSHowTo)?

---

### Post by banewman on 2008-02-12
Is portmap installed and running?

---

### Post by dan fisher on 2008-02-12
BINGO!

hadn't installed nfs-common or portmap

Can't recall if the initial NFS setup guide told me to do that

Thanks very much :biggrin:

---

