---
title: "cant mount cd"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-01-07
well i put the cd in the cdrom and it just sits there and spins and acts all goofy.  it wont mount the cd and i cant pull up anything from it.  its a windows program but ive got two cds for the same type of program and one of them works fine with WINE but the other one wont even load or read.  anyone know what i should try next

---

### Post by justifier on 2007-01-07
sudo mount /dev/hdc

---

### Post by houstonbofh on 2007-01-07
> **dragnazz5.0 said:**
> well i put the cd in the cdrom and it just sits there and spins and acts all goofy.  it wont mount the cd and i cant pull up anything from it.  its a windows program but ive got two cds for the same type of program and one of them works fine with WINE but the other one wont even load or read.  anyone know what i should try next
The program has nothing to do with it.  When you put it in, does the CD icon ever come up? Is it is normal data CD, or copy protected?  Is it clean, unscratched, and an original, or a burned CD?

---

### Post by dragnazz5.0 on 2007-01-09
its a brand new cd, just took it out of the package.  it is copy protected im sure since the program cost 75 bucks.  but that shouldnt keep my computer from reading it.  it does pull up the cd icon but it goes to the cd/dvd create folder
when i type sudo mount/dev/hdc it says command not found

---

### Post by WiseElben on 2007-01-09
You need a space between mount and /dev.

---

### Post by dragnazz5.0 on 2007-01-10
when i type sudo mount /dev/hdc this is what i get

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i know that it is a read only cd and thats all i want to do to....but how can i do it.  maybe the cd is bad?

---

### Post by dragnazz5.0 on 2007-01-11
anyone know what to do now?

---

### Post by goatflyer on 2007-01-11
```

sudo mount -t iso9660 /dev/hdc /media/cdrom0

```

If that fails, send us the output of

```

tail -n30 /var/log/messages

```

---

### Post by dragnazz5.0 on 2007-01-12
the first one didnt work so heres the message that i got with the second one

Jan 12 04:19:05 localhost -- MARK --
Jan 12 04:39:05 localhost -- MARK --
Jan 12 04:59:06 localhost -- MARK --
Jan 12 05:19:06 localhost -- MARK --
Jan 12 05:35:04 localhost kernel: [17775936.124000] Inbound IN=eth0 OUT= MAC=00:02:3f:79:16:a2:00:30:b8:c7:b7:10:08:00 SRC=72.29.75.99 DST=75.176.29.101 LEN=44 TOS=0x10 PREC=0x00 TTL=52 ID=17424 DF PROTO=TCP SPT=34396 DPT=22 WINDOW=5840 RES=0x00 CWR ECE SYN URGP=0
Jan 12 05:35:07 localhost kernel: [17775939.120000] Inbound IN=eth0 OUT= MAC=00:02:3f:79:16:a2:00:30:b8:c7:b7:10:08:00 SRC=72.29.75.99 DST=75.176.29.101 LEN=44 TOS=0x10 PREC=0x00 TTL=52 ID=17425 DF PROTO=TCP SPT=34396 DPT=22 WINDOW=5840 RES=0x00 CWR ECE SYN URGP=0
Jan 12 05:59:06 localhost -- MARK --
Jan 12 06:19:07 localhost -- MARK --
Jan 12 06:39:07 localhost -- MARK --
Jan 12 06:59:07 localhost -- MARK --
Jan 12 07:10:59 localhost kernel: [17781691.108000] Inbound IN=eth0 OUT= MAC=00:02:3f:79:16:a2:00:30:b8:c7:b7:10:08:00 SRC=83.10.236.235 DST=75.176.29.101 LEN=402 TOS=0x00 PREC=0x00 TTL=50 ID=55566 PROTO=UDP SPT=30991 DPT=1026 LEN=382
Jan 12 07:37:07 localhost kernel: [17783258.412000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 12 07:37:07 localhost kernel: [17783258.412000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 12 07:37:07 localhost kernel: [17783258.412000] ide: failed opcode was: unknown
Jan 12 07:37:37 localhost kernel: [17783288.600000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 12 07:37:37 localhost kernel: [17783288.600000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 12 07:37:37 localhost kernel: [17783288.600000] ide: failed opcode was: unknown
Jan 12 07:38:34 localhost exiting on signal 15
Jan 12 07:38:35 localhost syslogd 1.4.1#17ubuntu7: restart.
Jan 12 07:40:44 localhost kernel: [17783476.288000] Inbound IN=eth0 OUT= MAC=00:02:3f:79:16:a2:00:30:b8:c7:b7:10:08:00 SRC=133.11.195.90 DST=75.176.29.101 LEN=404 TOS=0x00 PREC=0x00 TTL=47 ID=27495 PROTO=UDP SPT=30991 DPT=1026 LEN=384
Jan 12 07:43:04 localhost gconfd (root-27692): starting (version 2.14.0), pid 27692 user 'root'
Jan 12 07:43:04 localhost gconfd (root-27692): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 12 07:43:04 localhost gconfd (root-27692): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 12 07:43:04 localhost gconfd (root-27692): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 12 07:43:04 localhost gconfd (root-27692): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 12 07:43:04 localhost gconfd (root-27692): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 12 07:44:42 localhost kernel: [17783713.764000] attempt to access beyond end of device
Jan 12 07:44:42 localhost kernel: [17783713.764000] hdc: rw=0, want=68, limit=4
Jan 12 07:44:42 localhost kernel: [17783713.764000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
Jan 12 07:44:42 localhost kernel: [17783713.888000] cdrom: This disc doesn't have any tracks I recognize!

---

### Post by dragnazz5.0 on 2007-01-12
anyone know what to do next?

---

### Post by goatflyer on 2007-01-13
Okay, the /var/log/messages mean Linux is confused about the format used on that cd.  It tried everything it knows about and comes up empty.

So my next question is: what happens when you put that cd into a windows machine and try to Explore it?  (if the program autostarts, just cancel, then goto My Computer, right-click cdrom drive and select Explore).

Does windows freak out, too?

---

### Post by houstonbofh on 2007-01-14
> **dragnazz5.0 said:**
> its a brand new cd, just took it out of the package.  it is copy protected im sure since the program cost 75 bucks.  but that shouldnt keep my computer from reading it.  
Some copy protection "works" by messing with the format of the CD.  That could be the case here.  (Or it may be something else, but I am suspicious)  What is the CD?

---

### Post by dragnazz5.0 on 2007-01-15
well ill have to take it to a buddies house because i dont have a windows machine here at all.  the program is jerry bickels chassis wizard for 4 link drag cars.  i just dont understand why it wont read this one but it will read the other disk in the set.

---

### Post by dragnazz5.0 on 2007-01-19
do i have any other option to see if this disk will read besides putting it into another computer?

---

### Post by shareMenaPeace on 2007-01-19
What is the output of the first command?

---

### Post by dragnazz5.0 on 2007-01-19
> **shareMenaPeace said:**
> What is the output of the first command?

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Jaidee on 2007-03-20
Any news on this? I'm having the same problem. It occured after I'd burned a CD. Here's my bug report:

[https://bugs.launchpad.net/ubuntu/+bug/94119]("https://bugs.launchpad.net/ubuntu/+bug/94119")

---

### Post by yioan on 2007-05-13
Hello,

I have exactly the same problem after I upgraded to feisty. Any ideas?

---

### Post by cody50 on 2007-05-13
recently i would be unable to mount CD's or just now my Flash Drive did not automount at all. however, I discovered last night if I rebooted it would work. I am currently on the same boot from last night and it is no longer working. i'm not sure why this happens.

---

### Post by Phaldor on 2007-11-26
Ok, here's my problem, and it's been happening for quite a while.  I'll put a disk in my drive tray (in my system, I've got two drives, a DVD/CDRW and a normal CDROM).  The first disk will work fine, it comes up, gives me an icon and I can get to the files, manipulate them in any allowable way, and I can even eject the disk when I'm done.  The second disk that I put in the drive makes the drive spin up, but never automount or even read the disk as far as I can tell.  It doesn't matter which drive I use first as the second disk can't be read from either drive.  I've had this problem on regular factory made CD's as well as the mini-DVD's from my camcorder.  Rebooting fixes the problems, but that's not a viable solution as my box is a web server, I simply can't be rebooting all the time.  I'm running Gusty as of this point, but had the problem with Feisty too.

What gives?

---

