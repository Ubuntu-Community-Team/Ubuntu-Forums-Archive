---
title: "ubuntu doesn't &quot;see&quot; my iPod"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-06-03
normally i connect my iPod to it's dock and it pops up; but i did that and ....nothing.

a little help would be appreciated.

thanks in advance.

---

### Post by thesonisshining on 2007-06-03
anybody have any clue how to fix this? i have tried to restart as well as shutdown the computer and start it back up again and now it won't even turn on.....i'm confused.

---

### Post by thesonisshining on 2007-06-03
now my iPod is completely dead it won't turn on it won't mount nothing. 

i really need some help please.

---

### Post by Lord Illidan on 2007-06-03
Battery problems?

---

### Post by thesonisshining on 2007-06-03
i have no idea.

---

### Post by thesonisshining on 2007-06-03
i was sitting here on my comp. and for no apparent reason the ipod just mounted and started charging......i'm really confused.

---

### Post by Lord Illidan on 2007-06-03
> **thesonisshining said:**
> i was sitting here on my comp. and for no apparent reason the ipod just mounted and started charging......i'm really confused.

probably a battery problem then.. was it at very low charge?

---

### Post by noodle43 on 2007-06-03
go to terminal and type
dmesg | tail 
post results

---

### Post by thesonisshining on 2007-06-03
> **Lord Illidan said:**
> probably a battery problem then.. was it at very low charge?

not that i know of

---

### Post by thesonisshining on 2007-06-03
> **noodle43 said:**
> go to terminal and type
dmesg | tail 
post results

chris@christopher-desktop:~$ dmesg | tail 
[ 2231.325250] sdb: Write Protect is off
[ 2231.325254] sdb: Mode Sense: 64 00 00 08
[ 2231.325257] sdb: assuming drive cache: write through
[ 2231.326870] SCSI device sdb: 495616 2048-byte hdwr sectors (1015 MB)
[ 2231.327495] sdb: Write Protect is off
[ 2231.327498] sdb: Mode Sense: 64 00 00 08
[ 2231.327500] sdb: assuming drive cache: write through
[ 2231.327503]  sdb: unknown partition table
[ 2231.351866] sd 2:0:0:0: Attached scsi removable disk sdb
[ 2231.351922] sd 2:0:0:0: Attached scsi generic sg2 type 0
chris@christopher-desktop:~$

---

### Post by thesonisshining on 2007-06-03
btw how do you type in this "|" character

---

### Post by Lord Illidan on 2007-06-03
> **thesonisshining said:**
> btw how do you type in this "|" character

It is on top of another character usually. On my keyboard, it is left of the Z button, on the \ button.

---

### Post by noodle43 on 2007-06-03
yup just as i thought,problem with the usb,

type
> dd if=/dev/zero of=/dev/hda

post results

---

### Post by thesonisshining on 2007-06-03
chris@christopher-desktop:~$ dd if=/dev/zero of=/dev/hda
dd: opening `/dev/hda': Permission denied
chris@christopher-desktop:~$

---

### Post by noodle43 on 2007-06-03
<snip>

---

### Post by thesonisshining on 2007-06-03
> **Lord Illidan said:**
> It is on top of another character usually. On my keyboard, it is left of the Z button, on the \ button.

got it now | thanks

---

### Post by thesonisshining on 2007-06-03
chris@christopher-desktop:~$ sudo dd if=/dev/zero of=/dev/hda
Password:
dd: writing to `/dev/hda': No space left on device
505657+0 records in
505656+0 records out
258895872 bytes (259 MB) copied, 9.63462 seconds, 26.9 MB/s
chris@christopher-desktop:~$

---

### Post by Nekiruhs on 2007-06-03
> **noodle43 said:**
> sudo dd if=/dev/zero of=/dev/hda?
DONT DO THAT! It ATTEMPTS TO ERASE YOUR HD!!
This poster is a worthless fool just check hi previous posts!

---

### Post by thesonisshining on 2007-06-03
> **Nekiruhs said:**
> DONT DO THAT! It ATTEMPTS TO ERASE YOUR HD!!
This poster is a worthless fool just check hi previous posts!

thank you i'm a noob at this. i guess you got those guys every where. they're more interested in destruction than edification.

---

