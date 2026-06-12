---
title: "NFS mounting issue..Please Help"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Rootcomputing on 2007-02-07
I am still learning some parts of linux, but I wanted to set up NSF to share my music on my server. 

I have installed nsf-kernel-server nad portmap on my server, they are running and seem to be functional. The configurations are below. 

root@x0ne:/# cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).

/storage 192.168.0.200(rw,sync)


root@x0ne:/# cat /etc/portmap
cat: /etc/portmap: No such file or directory
root@x0ne:/# cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       x0ne
192.168.0.10                                            x0ne

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

root@x0ne:/#cat /var/log/messages
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@x0ne:/# tail /var/log/messages
Feb  6 23:22:51 localhost kernel: [4660300.782000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Feb  6 23:29:05 localhost kernel: [4660674.538000] nfsd: last server has exited
Feb  6 23:29:05 localhost kernel: [4660674.538000] nfsd: unexporting all filesystems
Feb  6 23:32:13 localhost kernel: [4660862.016000] nfsd: last server has exited
Feb  6 23:32:13 localhost kernel: [4660862.016000] nfsd: unexporting all filesystems
Feb  6 23:32:13 localhost kernel: [4660862.020000] RPC: failed to contact portmap (errno -5).
Feb  6 23:43:21 localhost kernel: [4661530.610000] nfsd: last server has exited
Feb  6 23:43:21 localhost kernel: [4661530.610000] nfsd: unexporting all filesystems
Feb  6 23:43:21 localhost kernel: [4661530.611000] RPC: failed to contact portmap (errno -5).
Feb  7 00:05:13 localhost -- MARK --


I have performed a restart and the exportfs command. I also checked the privilages on the directory I am sharing along with all the files for NFS and they all have read and write access. 


Below configured on the client is , nfs-common with portmap. 

root@x0ne:~# cat /etc/hosts


127.0.0.1       localhost       x0ne
192.168.0.200   Server          x0ne  

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

root@x0ne:~# showmount -e 192.168.0.200
Export list for 192.168.0.200:
/storage 192.168.0.200

root@x0ne:~# mount -t nfs 192.168.0.200:/storage /mnt/server
mount: 192.168.0.200:/storage failed, reason given by server: Permission denied



I have tried everything, looked on forums, consulted with one of my friends who knows way more about linux then I do. I am in the Red Had academy and I talked with my teacher on how to set it up. I followed his directions and consulted all I could using google. If anyone can help I would appreciate it. Thanks in advance.

---

### Post by PriceChild on 2007-02-07
*bump*

---

### Post by renzokuken on 2007-02-07
i had this exact same issue last night. i havent got round to solving it yet, but from what i understand, it has something to do with user permissions on the server. i'll lett you know how my attempts go.

is "storage" by any chance a seperate hard drive/partition to your root ( / ) installation on the server?

---

### Post by Rootcomputing on 2007-02-07
It does infact look like storage is on its own partition.

root@x0ne:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              8883628    642616   8241012   8% /
tmpfs                   258244         0    258244   0% /dev/shm
tmpfs                   258244     12588    245656   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda1                96312     48684     47628  51% /boot
/dev/md0              72161504  28415724  43745780  40% /storage


root@x0ne:~# fdisk -l

Disk /dev/hda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          12       96358+  83  Linux
/dev/hda2              13        1118     8883945   83  Linux
/dev/hda3            1119        1245     1020127+  82  Linux swap / Solaris

Disk /dev/sda: 36.9 GB, 36951490048 bytes
255 heads, 63 sectors/track, 4492 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4492    36081958+  fd  Linux raid autodetect

Disk /dev/sdb: 36.9 GB, 36951490048 bytes
255 heads, 63 sectors/track, 4492 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4492    36081958+  fd  Linux raid autodetect

Disk /dev/md0: 73.8 GB, 73895641088 bytes
2 heads, 4 sectors/track, 18040928 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table



If youre online, my screen name is rebrokenglass. I am trying to figure it out still and if you manage to get it. PM me, post or IM me. Thanks

---

### Post by renzokuken on 2007-02-08
i managed to get mine working last night.

turned out i wasn't specifying the correct location of the folder i wanted to share on my server (coincidentally also called storage)

on my server/desktop pc, i have a seperate harddrive i use for storing video and music. this harddrive is automounted by fstab to the folder /media/storage

initially i was trying the mount command

```
sudo mount 192.168.1.2/24:/storage /storage
``` (where i had created a folder called storage in the root directory / of my client)

anyway, that didnt work and then i realised i was being stupid and the correct command should have been

```
sudo mount 192.168.1.2/24:[color=red]/media[/color]/storage /storage
```

where i was actually using the full mount path of the folder on my server.

i have no idea if this helps, but i said i would get back to you with how it went, and that was my only problem

---

