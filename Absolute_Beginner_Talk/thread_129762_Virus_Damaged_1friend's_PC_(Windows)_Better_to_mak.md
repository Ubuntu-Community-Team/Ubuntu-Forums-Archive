---
title: "Virus Damaged 1friend's PC (Windows): Better to make hdd backup with dd or ntfsclone?"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-14
Hi, 

The purpose is to make a big file backup of the damaged partition? 
Once the file created (raw disk file) or conmpressed, I am gonna recover the data with one windows program 
(I am using since years).
  
So, the question is as follows: 
Should it be used       dd            or clonentfs  to make this backup of partition ?
  
  
For my point of vue, I am damn damn recommanding dd if ... of .... bla bla ...
(dd ). I am right ? 

Thank you, 

Greetings, 

Pat'

---

### Post by cwaldbieser on 2006-02-14
[QUOTE=patrick295767]Hi, 

The purpose is to make a big file backup of the damaged partition? 
Once the file created (raw disk file) or conmpressed, I am gonna recover the data with one windows program 
(I am using since years).
  
So, the question is as follows: 
Should it be used       dd            or clonentfs  to make this backup of partition ?
  
  
For my point of vue, I am damn damn recommanding dd if ... of .... bla bla ...
(dd ). I am right ? 

Thank you, 

Greetings, 

Pat'[/QUOTE]

The one drawback of dd over tools like Ghost4Linux or GNU Parted is that it backs up the whole drive-- even the empty space.

---

### Post by patrick295767 on 2006-02-15
xfs_repair exists too..

I guess better make a dd backup first.

---

### Post by davmac on 2006-02-15
Patrick,

Have you considered something like Knoppix for this? I've had great success recovering windows boxes by booting up with Knopppix and then recovering the data on to a USB drive.

Hope this helps,

Dave Mac

---

### Post by patrick295767 on 2006-02-15
[QUOTE=davmac]Patrick,

Have you considered something like Knoppix for this? I've had great success recovering windows boxes by booting up with Knopppix and then recovering the data on to a USB drive.

Hope this helps,

Dave Mac[/QUOTE]
  
The friend tried knoppix, and uses it now indeed;

No, the virus damaged the filesystem of the files . U cannot read unfortunately anythg from it. It's not a trivial virus this one ! Even the norton updated cannot find it... I dont know , have no idea where he was able to get such virus.

For me, that's still a bit strange. I never got any prob with all my pc's ... hmm   :-k 
  
Thank you Dave ! Btw, You are in my msn buddy list since long time & we never chat with each other :-) 

Have a good Day & Greetings from Belgium, 

Patrick
===
(U tried the OS x ?)

---

### Post by patrick295767 on 2006-02-17
I used : 

```
dd If=/dev/hda2 conv=sync,noerror bs=1k | gzip | dd of=/mnt/backup.img.gz
```

After one day of processing of the PC ... I waited long.

This morning:
I get one error in the gz file .... 
Prob with packing and end of file ....?
(when I un-gzip the backup file)

What should I do ?



===
(virus damaging very well the /dev/hda2)

---

