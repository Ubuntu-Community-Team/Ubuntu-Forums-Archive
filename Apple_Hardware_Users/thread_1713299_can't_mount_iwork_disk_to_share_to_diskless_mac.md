---
title: "can't mount iwork disk to share to diskless mac"
date: 2011-03-23
forum: Apple Hardware Users
---

### Post by zarthon on 2011-03-23
I am trying to mount my iWork disk on my self-built desktop running 64 bit Ubuntu 10.10. I have a mac mini server without a dvd or cd drive. I want to install iWork. 
For some reason the disk will not mount even using hfsutil hmount command. It says the disk is not hfsplus. Mount says the disk is not iso9660 and won't mount it with -t auto. 
I am wondering if it's a modified iso9660 format and I need to specify options / apple extensions.
**:confused:**
The drive works with other media but I can run suggested tests.

Any ideas?
Thanks !

---

### Post by zarthon on 2011-03-26
bump

---

### Post by linuxuser12345 on 2011-03-26
I am not even sure you CAN run Mac programs on Ubuntu

---

### Post by zarthon on 2011-03-27
> **linuxuser12345 said:**
> I am not even sure you CAN run Mac programs on Ubuntu

Thanks for your reply.
You can not run programs written for Mac OS on Ubuntu because they rely on the Mac Os libs. 

I am trying to mount the volume and share the DVD over my lan so that i can install iWork on my Mac Mini. It has no DVD drive but runs Mac OS Server 10.6.6.

All i am doing in Ubuntu is mounting the volume and using the nsf share i've already set up.

---

### Post by zarthon on 2011-03-30
I have tried to mount it as /dev/dvd and /dev/dvd0 /dev/dvd1 with hmount and this has failed. 

Any ideas ? Feel free to share. It does not have to work, or even make much sense. I am glad to feel that i am not totally alone on this one.

Has no one else gone out and bought a Mac Mini server assuming that they could just share over discs from there Ubuntu system ? ?

I have determined that I can read data from the disk in raw mode. I read and inspected about the first 12 mb of the disk which is mostly 0's. Most of the other information is readable text. It seems to say that it's an HFS disk not an ISO. 


This should work !  ! ! 
Come on ! Ubuntu is unable to mount a major disc format.... Really ?

Maybe the answer is to get Fedora running in another LVM volume and see if that works. If so then I could post a bug against the ubuntu hfs package, if it doesn't then i could install from source... hum that is easier ... if I were not planning on the Fedora image anyway... 
Thanks for any input you have ! 
What do you think is a good next thing to try when i have a few extra mintues between main projects ?

;)

---

### Post by zarthon on 2011-04-06
#mount -t iso9660 /mnt/dvd /mnt/foo
mount: special device /mnt/dvd does not exist
#mount -t iso9660 /dev/dvd /mnt/foo
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

#mount -t hfsplus /dev/dvd /mnt/foo
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

#hmount /dev/dvd /mnt/foo
hmount: /dev/dvd: not a Macintosh HFS volume (Invalid argument)
#hmount /dev/cdrom /mnt/foo
hmount: /dev/cdrom: not a Macintosh HFS volume (Invalid argument)
#hmount /dev/dvd0 /mnt/foo
hmount: /dev/dvd0: error opening medium (No such file or directory)
#hmount /dev/dvd1 /mnt/foo
hmount: /dev/dvd1: error opening medium (No such file or directory)

It occurred to me that since it's a dvd it could be encrypted in some way like a movie disk. The data I can see from reading raw data from the device does not seem encrypted but it also does not look like a normal disk header either. 
I have successfully mounted and played a video DVD, mounted ISOs, written ISOs played audio cd's and used sound juicer to save music, so it's not hardware drivers or the hardware. 
iWork  is a piece of work. looks like i will pack up my ma mini and take it into the Apple store for installation.
I just don't feel responsible not submitting a bug against mount or hdparam or find out what proprietary limitation stops the disk from mounting. I think i will also post a reference to the thread on the Apple forums.

---

### Post by zarthon on 2011-04-07
I finally worked around the failure of Ubuntu linux to mount the iwork disk.
The solution should have dawned on me earlier.
From my Ubuntu workstation with the DVD-RW drive I copied an image of the disk to the Mac Mini server over the network.
Double clicking on the img file in Mac OS 10.6 opened it like it was the disk itself and the install process was successful.

```

#dd bs=4096 if=/dev/dvd of=/home/johnh/sysimg/iwork.img
142608+0 records in
142608+0 records out
584122368 bytes (584 MB) copied, 113.754 s, 5.1 MB/s
# 

```

If anyone has a similar issue I'd be happy to post / msg more details. Just message me.

---

