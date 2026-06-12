---
title: "Samba mount problems"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-29
I am trying to mount the SharedDocs folder on my wifes XP laptop.
A buddy gave me this line of code but when I execute it I get this error

charles@charles-desktop:/etc/samba$ sudo mount -t cifs //MICHELLE/SharedDocs /etc/samba -o username=Michelle
mount: wrong fs type, bad option, bad superblock on //MICHELLE/SharedDocs,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I checked the output of dmesg|tail but dont undersand it at all...

charles@charles-desktop:/etc/samba$ dmesg | tail
[17217564.880000] Unknown OutputIN= OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241 .255 LEN=229 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=209 
[17217734.880000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.176.1 DST=172.16.176.2 55 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17217734.880000] Unknown OutputIN= OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241 .255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17218034.880000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.176.1 DST=172.16.176.2 55 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17218034.880000] Unknown OutputIN= OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241 .255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17218284.880000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.176.1 DST=172.16.176.2 55 LEN=229 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=209
[17218284.880000] Unknown OutputIN= OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241 .255 LEN=229 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=209 
[17218334.880000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.176.1 DST=172.16.176.2 55 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17218334.880000] Unknown OutputIN= OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241 .255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17218391.372000]  CIFS VFS: cifs_mount failed w/return code = -22

This is the tail of my syslog.

charles@charles-desktop:/var/log$ tail syslog
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] nmbd/nmbd_namequery.c:query_name(237)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   query_name: Failed to send packet trying to query name MOOREHOME<1d>
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] libsmb/nmblib.c:send_udp(791)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   Packet send failed to 192.168.241.255(137) ERRNO=Operation not permitted
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   send_netbios_packet: send_packet() to IP 192.168.241.255 port 137 failed
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] nmbd/nmbd_namequery.c:query_name(237)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   query_name: Failed to send packet trying to query name MOOREHOME<1d>
Sep 29 09:45:15 charles-desktop kernel: [17218634.888000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.176.1 DST=172.16.176.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 29 09:45:15 charles-desktop kernel: [17218634.888000] Unknown OutputIN= OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58

---

### Post by LotsOfPhil on 2006-09-29
I use "-t smbfs" but CIFS and SMB are the same thing, so that probably isn't a problem.

One big thing, change your mount point! You are mounting it in /etc/samba. Make a new directory (somewhere else) and mount it there.

Are you sure everything is set up right on the XP box? As long as you have a valid location (//MICHELLE/SharedDocs) and a valid username/password (Michelle/none) it should be okay on the Linux side.

I would change cifs to smbfs.

---

### Post by dca on 2006-09-29
Make sure the XP firewall is turned off completely.  Set sharing for entire hard drive on XP machine, and use the 'Network Servers' dealie in PLACES and see if the PC is visible on the network?  I don't know, I'm not much help...

---

### Post by qpieus on 2006-09-29
Go look here:
[http://steve.kargs.net/applications/samba-cifs-and-ubuntu-linux-server/]("http://steve.kargs.net/applications/samba-cifs-and-ubuntu-linux-server/")
for a similar program. According to this article, you may need to install smbfs:```
sudo apt-get install smbfs
```There are some other links there that may help you too.

---

### Post by charles.g.moore on 2006-09-30
I am at a loss here I have shared the entire D: on her puter and changed the command per lotsofphil's instructions but still nothing when I try to mount I still get this error

charles@charles-desktop:/dev$ sudo mount -t smbfs //MICHELLE/michellesD /etc/samba -o username=Michelle
mount: wrong fs type, bad option, bad superblock on //MICHELLE/michellesD,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by chrisfay on 2006-09-30
Like qpieus said, you need to install the samba file system.

```
sudo apt-get install smbfs
```

You can also verify that the share is available by:

```
sudo smbtree
```

Try adding the share into /etc/fstab then:

```
sudo mount -a
```

---

### Post by LotsOfPhil on 2006-09-30
I still think you should change the /etc/samba to a different directory.

Also, try "ping -c 1 MICHELLE" Your path to the share needs to be right.

---

### Post by crazymonkey on 2006-09-30
> **charles.g.moore said:**
> 
charles@charles-desktop:/etc/samba$ dmesg | tail
[17217564.880000] Unknown OutputIN= **OUT=vmnet1** SRC=192.168.241.1 DST=192.168.241 .255 LEN=229 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=209 
[17217734.880000] Unknown OutputIN= **OUT=vmnet8** SRC=172.16.176.1 DST=172.16.176.2 55 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58

charles@charles-desktop:/var/log$ tail syslog
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] nmbd/nmbd_namequery.c:query_name(237)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   query_name: Failed to send packet trying to query name MOOREHOME<1d>
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] libsmb/nmblib.c:send_udp(791)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   Packet send failed to 192.168.241.255(137) ERRNO=Operation not permitted
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   send_netbios_packet: send_packet() to IP 192.168.241.255 port 137 failed
Sep 29 09:45:15 charles-desktop nmbd[5128]: [2006/09/29 09:45:15, 0] nmbd/nmbd_namequery.c:query_name(237)
Sep 29 09:45:15 charles-desktop nmbd[5128]:   query_name: Failed to send packet trying to query name MOOREHOME<1d>
Sep 29 09:45:15 charles-desktop kernel: [17218634.888000] Unknown OutputIN= **OUT=vmnet8 SRC=172.16.176.1 DST=172.16.176.255** LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 29 09:45:15 charles-desktop kernel: [17218634.888000] Unknown OutputIN= **OUT=vmnet1 SRC=192.168.241.1 DST=192.168.241.255** LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58

VMNET 1 and 8 are VMWare interfaces for the VMware NAT and host-only networking. It seems that for unknown reasons the request are sent to your VMware interfaces... :-k 

Maybe you should try to send the request to the IP of Michelle instead of the name ```
sudo mount -t cifs //192.168.?.?/SharedDocs /etc/samba -o username=Michelle
```

Replace 192.168.?.? by the computer IP.

It would also be interesting to see the beginning of the logs maybe the error is before what the tail command covers...

---

### Post by charles.g.moore on 2006-10-01
crazymonkey,
that did the trick I am now in her system, i hadnt noticed that my vmware was where the requests were being sent.

Thank you so much!!!

Now my question is how do i unmount it using umount?  I keep getting this:

charles@charles-desktop:/etc/samba$ sudo umount /etc/samba
umount: /etc/samba: device is busy
umount: /etc/samba: device is busy

---

### Post by crazymonkey on 2006-10-01
> **charles.g.moore said:**
> crazymonkey,
that did the trick I am now in her system, i hadnt noticed that my vmware was where the requests were being sent.

Thank you so much!!!

Now my question is how do i unmount it using umount?  I keep getting this:

charles@charles-desktop:/etc/samba$ sudo umount /etc/samba
umount: /etc/samba: device is busy
umount: /etc/samba: device is busy

I'm glad that worked!

Now for "the device is busy" problem it is because some process is still accessing the mounted share. Make sure you don't have any open files from the share on your desktop before unmouting. There are two option you might want to add to the umount command :

```
sudo umount **-r** /etc/samba
```
With the -r option in case unmounting fails, it will try to remount read-only. After it is remounted read-only try to unmount it again without the -r option.

```
sudo umount **-l** /etc/samba
```
That is lazy unmount, it will remove the the share from /etc/samba but will only remove other references when the device is not busy anymore. That means for you the share is being unmounted but the process that are using it can still access it until they are done.

---

