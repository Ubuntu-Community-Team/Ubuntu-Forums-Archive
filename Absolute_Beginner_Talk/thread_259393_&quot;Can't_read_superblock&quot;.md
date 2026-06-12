---
title: "&quot;Can't read superblock&quot;"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-09-17
Hello,
There must be somebody on planet Earth who invented this error message:
```
mount: /dev/pktcdvd/0: [COLOR="Red"]can't read superblock[/COLOR]
```
It seems 
There is a mounting problem and 
There must be somebody on planet Earth who knows what causes this message! And
There must be somebody on planet Earth who knows what to do to fix it!

How can I contact him? Are there costs involved to get a solution? 
I'm stuck since more than a week now with this...any idea, thought, advice is highly appreciated.:confused:

---

### Post by christhemonkey on 2006-09-17
This is a mounting problem with your cd/hard drive.

Can you give the output of:
```
dmesg | tail 
```
and
```
cat /var/syslog
```
?

---

### Post by Cariboo1938 on 2006-09-17
Thank you chris for taking time. Here are the terminal printouts you were looking for. The /syslog file has these lines repeated with different time figures.


> **christhemonkey said:**
> This is a mounting problem with your cd/hard drive.

Can you give the output of:
```
dmesg | tail 
```

> owner@Owner-Desktop:~$ sudo dmesg | tail

[  173.770541] Bluetooth: RFCOMM ver 1.7
[  181.731176] cdrom: hda: mrw address space DMA selected
[  181.732387] cdrom open: mrw_status 'not mrw'
[  181.860349] cdrom: hda: mrw address space DMA selected
[  181.861988] cdrom open: mrw_status 'not mrw'
[  181.878101] UDF-fs: No VRS found
[  230.371022] CSLIP: code copyright 1989 Regents of the University of California
[  230.376405] PPP generic driver version 2.4.2
[  232.198249] PPP BSD Compression module registered
[  232.222755] PPP Deflate Compression module registered


> **christhemonkey said:**
> 
and
```
sudo cat /var/syslog
```
> owner@Owner-Desktop:~$ sudo cat /var/syslog
cat: /var/syslog: No such file or directory

But: 
> ```
sudo cat /var/log/syslog
```[QUOTE]
Sep 17 11:25:39 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 3
Sep 17 11:25:41 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 8
Sep 17 11:25:49 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 15
Sep 17 11:26:04 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 9
Sep 17 11:26:13 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 10
Sep 17 11:26:23 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 16
Sep 17 11:26:40 localhost dhclient: No DHCPOFFERS received.
Sep 17 11:26:40 localhost dhclient: No working leases in persistent database - s leeping.
Sep 17 11:30:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 8
Sep 17 11:30:13 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 9
Sep 17 11:30:22 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 13
Sep 17 11:30:35 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 9
Sep 17 11:30:44 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 7
Sep 17 11:30:51 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port  67 interval 15
Sep 17 11:31:07 localhost dhclient: No DHCPOFFERS received.
Sep 17 11:31:07 localhost dhclient: No working leases in persistent database - s leeping.
owner@Owner-Desktop:~$
[/QUOTE]Just in case you want to see /etc/fstab:
> 
# /etc/fstab: static file system information.
#<file system> <mount point>   <type>   <options>          <dump>  <pass>

## Linux 'Ubunu 6.06'
proc             /proc           proc     defaults             0       0
/dev/sda2        /                ext3    defaults,errors=remount-ro 0       1
/dev/sda3        /Storage         ext3    defaults             0       2
/dev/sda1        /boot            ext3    defaults             0       2
/dev/sda5        /home            ext3    defaults             0       2
/dev/sda6        /usr             ext3    defaults             0       2
/dev/sda7        /var             ext3    defaults             0       2
/dev/sda8        none             swap    sw                   0       0

/dev/hda      /media/cdrom1    iso9660,udf   rw,users,noauto       0      0
/dev/hdb      /media/cdvdrw    iso9660,udf   rw,users,noauto       0      0

##Special packet writing device
/dev/pktcdvd/0  /media/udf0      udf    users,noauto,noatime,utf8  0      0
/dev/pktcdvd/1  /media/udf1      udf    users,noauto,noatime,utf8  0      0

## Windows 'XP Home'
#/dev/sdb1        /mnt/Windows  HPFS/NTFS    ro,defaults                0      1
#/dev/sdb2        /mnt/User     HPFS/NTFS    rw,defaults,users,noauto,  0      2


---

### Post by christhemonkey on 2006-09-17
Do you have a disc in your cd drive?


And thanks for noticing my typo.... lol

---

### Post by Cariboo1938 on 2006-09-18
> **christhemonkey said:**
> Do you have a disc in your cd drive?
And thanks for noticing my typo.... lol#-o No, **I didn't** have a CD inserted in my drive when I executed the command
*sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0*
Thank you Chris, you are a genius! 
I made one of those stupid mistakes doing things without exactly knowing what I do!!! 
Now I know: 
I had to mount a CD and not the CD drive, because the CD has the File System on it I wanted to use...UDF.

So, the solution to my problem with the 'not readable superblock' is:
When executing the command

*sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0*

the formatted CD has to be inserted in the corresponding drive!

Many, many thanks, Chris, you cannot imagine how you helped me. 
Thanks again=D> 
Cariboo

---

### Post by christhemonkey on 2006-09-18
No problem!

---

