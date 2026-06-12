---
title: "Slow Home directory load"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by sbrody88 on 2007-03-02
Hi, I've had Ubuntu for a few months now, with no major problems.  However, recently (in the last week or so) I've been having a problem where (almost) everytime I try to go to my home directory, it takes an extrememly long time to load, or doesn't load at all unless I close the File Browser and try to open it again.  Sometimes it takes 4 or 5 tries to get it to load.  I can get every other directory in my File System to load fine, it's just the home folder.  I recently mounted an smbfs filesystem to my home directory using smbmount, I don't know if that could have anything to do with it or not.  Can anyone help me sort this out?

---

### Post by moshuptrail on 2007-03-02
I wonder if you have some bad blocks.
Try typing dmesg at the command line.
You could also type: tail /var/log/syslog
If either one has odd output, post it here.

---

### Post by sbrody88 on 2007-03-03
tail /var/log/syslog outputted the following:

Mar  3 12:54:25 localhost dhclient: DHCPACK from 128.148.128.15
Mar  3 12:54:25 localhost dhclient: bound to 138.16.29.187 -- renewal in 2985 seconds.
Mar  3 13:17:01 localhost /USR/SBIN/CRON[7471]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  3 13:27:42 localhost kernel: [17338535.420000] smb_add_request: request [c84afec0, mid=272] timed out!
Mar  3 13:27:42 localhost kernel: [17338535.420000] smb_lookup: find //s failed, error=-5
Mar  3 13:27:47 localhost kernel: [17338540.708000] SMB connection re-established (-5)
Mar  3 13:29:03 localhost kernel: [17338616.376000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=194.109.161.58 DST=138.16.29.187 LEN=60 TOS=0x00 PREC=0x00 TTL=45 ID=58632 DF PROTO=TCP SPT=28328 DPT=6881 WINDOW=5840 RES=0x00 SYN URGP=0
Mar  3 13:29:10 localhost kernel: [17338622.940000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=70.177.66.222 DST=138.16.29.187 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=40058 DF PROTO=TCP SPT=62952 DPT=46413 WINDOW=65535 RES=0x00 ACK URGP=0
Mar  3 13:29:16 localhost kernel: [17338629.104000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=82.1.96.218 DST=138.16.29.187 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=26227 DF PROTO=TCP SPT=63068 DPT=35457 WINDOW=65535 RES=0x00 ACK URGP=0
Mar  3 13:29:16 localhost kernel: [17338629.132000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=70.177.66.222 DST=138.16.29.187 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=40886 DF PROTO=TCP SPT=62952 DPT=46413 WINDOW=65535 RES=0x00 ACK URGP=0


while dmesg outputted something that was REALLY long, and exceeded the character limit of my post to this thread.:(  So, if there's a specific portion of that output you'd like to see, let me know and I'll post it.

---

### Post by moshuptrail on 2007-03-04
Two tracks to follow:
1) I see you are running Samba.  Do you have anything linked in your home folder to a Samba share?  I was just thinking that maybe if Samba wasn't fully operational (see errors in the syslog) it might  cause a delay.
2) do the dmesg command immediately after you experience the slowness.  Then post the last 20 lines only.  Alternately, type dmesg | tail, which gives just the last 10 lines, but if you are having HD issues it will show.

I didn't see any smoking guns in the syslog.  Just a few Samba errors.  You might try turning off Samba and see what happens.

Sorry to take so long getting back.

p.s. I just noticed your comment about Samba in the original post.  Hmmm.  Follow that lead.  You might be onto something.

---

### Post by sbrody88 on 2007-03-04
The last 20 lines of output from dmesg after I had the slow load are as follows:

[17189361.660000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=18754 DF PROTO=TCP SPT=63964 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189364.652000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=18773 DF PROTO=TCP SPT=63964 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189370.656000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=104 ID=18799 DF PROTO=TCP SPT=63964 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189463.996000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=200.104.22.33 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=28461 DF PROTO=TCP SPT=62996 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189473.012000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=200.104.22.33 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=28649 DF PROTO=TCP SPT=62996 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189478.936000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=20536 DF PROTO=TCP SPT=64056 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189481.944000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=20582 DF PROTO=TCP SPT=64056 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189487.948000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=104 ID=20641 DF PROTO=TCP SPT=64056 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189525.008000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=74.71.79.227 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=13863 DF PROTO=TCP SPT=3513 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 
[17189527.872000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=74.71.79.227 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=13873 DF PROTO=TCP SPT=3513 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 
[17189533.888000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=74.71.79.227 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=13911 DF PROTO=TCP SPT=3513 DPT=6881 WINDOW=65535 RES=0x00 SYN URGP=0 
[17189738.864000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=27718 DF PROTO=TCP SPT=60142 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189741.100000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=200.104.22.33 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=2369 DF PROTO=TCP SPT=63543 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189741.524000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=27829 DF PROTO=TCP SPT=60142 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189744.100000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=200.104.22.33 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=2479 DF PROTO=TCP SPT=63543 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189746.380000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=128.148.128.15 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=60 ID=5480 DF PROTO=TCP SPT=50952 DPT=7 WINDOW=49640 RES=0x00 SYN URGP=0 
[17189747.756000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=24.28.23.123 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=104 ID=28090 DF PROTO=TCP SPT=60142 DPT=6882 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189750.092000] Inbound IN=eth0 OUT= MAC=00:d0:59:34:34:91:00:09:e8:24:53:ff:08:00 SRC=200.104.22.33 DST=138.16.29.187 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=2627 DF PROTO=TCP SPT=63543 DPT=6881 WINDOW=8192 RES=0x00 SYN URGP=0 
[17189911.100000] smb_add_request: request [c6c90e80, mid=11] timed out!
[17189915.768000] smb_add_request: request [c6c90d80, mid=12] timed out!
[17189916.284000] SMB connection re-established (-5)


If my SMBmount is the problem, is there a way to fix it without removing the mount?

---

