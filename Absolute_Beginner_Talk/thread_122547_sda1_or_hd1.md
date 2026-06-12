---
title: "sda1 or hd1 ??"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by SilverTab on 2006-01-27
Ok this might be a stupid question (it probably is...)

but I just got a new computer (my other one was stollen :evil: )

and on this one my hard disk (and partitions) are labled sdax

example:
/dev/sda1   *           1       27851   223713126    7  HPFS/NTFS
/dev/sda2           27852       30262    19366357+  83  Linux
/dev/sda3           30263       30401     1116517+  82  Linux swap / Solaris


I rememeber on my other computer they were labled hda1, hda2 etc etc...


what is the difference between sda and hda ???

---

### Post by dueY on 2006-01-27
Is your new computer SATA?

---

### Post by SilverTab on 2006-01-27
good question!

I never heard of SATA before, but after doing some research, I found out some info about SATA on Seagate's website... AND my new hard drive (250gb) is ... a seagate....

so, Im thinking it could be SATA???

---

### Post by SilverTab on 2006-01-27
mmm also...after taking a look at the device manager (System >> Administration >> Device Manager)  I noticed that more than half of my peripherals are marked as unknown....not sure if it's a problem?? Everything seems to run fine...

---

### Post by Madpilot on 2006-01-27
sdaX does mean that those partitions are on a SATA drive. My only hard drive currently is a Maxtor SATA 120Gb, so I've got sda1 & sda2.

If you had a 2nd SATA drive, it's partitions would be sdb1, sdb2, etc.

sd-X is actually used for more than just SATA drives - USB devices are mounted as sd-X as well.

---

### Post by SilverTab on 2006-01-27
gotcha! thanks :)

my HD is in fact, SATA!

I'm just so used to type hda1  that when I was told I had no device at /dev/hda1  I freaked out LOL

---

### Post by rfruth on 2006-01-27
I asked a similiar (sda1 ?) question on alt.linux and yes device manager has lots of unknowns for me too so don't sweat it 
[PHP]anyone wrote:

>> 
>> Ubuntu 5.10 (Breezy) refers to my one and only ATA hard disk as SCSI
>> http://www.rfruth.net/resume/computers/breezy/rfbreezy.txt
>> even though I have *no* SCSI devices, no problem with install or
>> operation, this is a cosmetic 'problem' anyone else noticed this ?
>> 
>> 


In Linux will SATA (and PATA) disks appear as SCSI devices, eg. /dev/sda
or /dev/sdb.

$ cat /proc/scsi/scsi

The driver has a SCSI <-> ATA Translation layer (SATL) that handles the
minor differences between SATA and SCSI command sets. I guess, the
translation is done by libATA module.

$ find /lib/modules/$(uname -r)/  -name "*libata*"

SCSI <-> ATA Translation (SAT) is a standard of http://www.t10.org
--------------

You can mix of pure SCSI and ATA devices in one computer.


//moma
  http://www.futuredesktop.org/how2burn.html#Ubuntu  <--Vital Ubuntu
resources

[/PHP]

---

