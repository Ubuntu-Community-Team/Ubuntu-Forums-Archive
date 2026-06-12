---
title: "autofs don't work"
date: 2011-09-09
forum: Any Other OS
---

### Post by zkab on 2011-09-09
I installed Linux Mint (Katya 64-bit and Ubuntu based) on a new computer and it doesn't automount (autofs) my NFS shares.
Have another computer running Fedora and it works OK ... actually copies all auto.* from Fedora to Katya.
Here is what I have:
1) auto.master
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
/nfs	/etc/auto.nfs
/cifs	/etc/auto.cifs
2) auto.nfs
Arkiv_X	 -fstype=nfs,rw,hard,intr,rsize=65536,wsize=65536 arkiv-x:/home
Arkiv_Disk	-fstype=nfs,rw,hard,intr,rsize=65536,wsize=65536 arkiv-x:/Arkiv_Disk/home
NSLU2	 -fstype=nfs,rw,hard,intr,rsize=65536,wsize=65536 NSLU2:/home/raivo/
NSLU2_Disk_2	-fstype=nfs,rw,hard,intr,rsize=65536,wsize=65536 NSLU2:/disk_2
3) The service autofs runs OK
sudo service autofs restart
autofs start/running, process 3477
4) When I mount NFS shares via fstab (as a test) it works OK ... so there is no problem with the NFS server ... the Fedora computer can access the shares without no problems.
My fstab in Katya:
arkiv-x:/home	/nfs	nfs	rw,hard,intr,rsize=65536,wsize=65536	0 0

Why can't I get autofs working in Katya ?

---

### Post by Perfect Storm on 2011-09-09
Moved to Other OS/Distro Talk.

---

