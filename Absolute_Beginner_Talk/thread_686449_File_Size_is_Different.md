---
title: "File Size is Different"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-03
I just downloaded a Debian DVD iso into my home folder and then moved it into my external hard drive. On my home folder, the iso appears as a 4.4gb raw cd image, but on my external hard drive it is only 4.0 gb. My external hard drive has 42gb free, so what is wrong?

---

### Post by szymon_g on 2008-02-03
what kind of filesystem you have got on external drive :?

btw, don't forget to check md5sums.
ethc or lenny :? or maybe sid :>?

---

### Post by intense.ego on 2008-02-03
I just checked and the External HDD is vfat (i'm not sure, but i think that is what you wanted to know). i downloaded using a download manager, so i didn't think it would be a problem but i will still check.

EDIT: how do you use md5checksums to check?

---

### Post by szymon_g on 2008-02-03
i'm afraid, but Vfat (or fat32) doesn't accept so big files :/
you can change it to ntfs - ubuntu doesn't have problems with reading/writing into it
or into ext2/3 or other linux filesystem (but it wont be accessible for windowsxp system)
and, btw, checking md5sums of isos is, i'm afraid,  a mandatory action. it really matters.

you can check checksums by typing

md5sum file.iso - you have to have md5sum file (it have to be on the same directory from with you downloaded iso file)

be prepared- it will take some time

---

### Post by intense.ego on 2008-02-03
how would i go about changing into ntfs?

---

### Post by szymon_g on 2008-02-03
the easiest way- is under windowsxp, just right-click on drive partition check proporties and find it (sorry, i have no windowsxp on my machines, so i wont tell you when *exactly* it is)
in the ubuntu is gparted- easy, graphical tool for it
of course, when you change fsystem, you will lose all unsaved-on-another-partition data on this partition :/

---

### Post by intense.ego on 2008-02-03
Firstly, i ran md5sum on the iso and got a strange number:
```
ee9353e86b9ce31d0a6bd93c884b6dd2  debian-40r2-i386-DVD-1.iso

```
what does this mean?

My external hard drive is not partitioned so I don't believe there should be any data lost. 

Can I use gparted straight from ubuntu or do i have to use a livecd?

---

### Post by szymon_g on 2008-02-03
you prabably get them from this site

[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-dvd/](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-dvd/)

in this file
[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-dvd/MD5SUMS](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-dvd/MD5SUMS)
are writtem md5sums of isofiles. your file is downloaded correctly, as you can see.

when you're downloading any important data (like cd/dvd images) you always should check md5sum/sha1sum of this files and compare it with them from original's.
if md5sum of downloaded file differs from this original one, that means that this file was downloaded incorrectly, and during using this image some unexpected errors (prabably) will happend. in short: use on your own risk :>


as you wrote, there is vfat /fat32/ filesystem- sou there is at least one partition/logical disc on it.
when you will be putting new filesystem on this disc/partition, you will lose all data on it.
and yes, you can use ubuntu's qparted- this one installed on your harddrive

---

### Post by intense.ego on 2008-02-03
> **szymon_g said:**
> 
when you will be putting new filesystem on this disc/partition, you will lose all data on it.


Could you please clarify, i didn't quite understand.

---

### Post by szymon_g on 2008-02-03
ok, i'll try to clarify (as far as my english will let me to do that ;p).
whan you have a external drive (on usb, i assume- but it doesn't really metter now) you may have 1 or more logical partitions /something like C: D: E: in dos/windows/.
on each partition- if you wanna use it instead of just having it- must be a filesystem (ntfs, fat12,16,32- on windows/dos, ext2,3,raiserfs,xfs,jfs - this are the most common linux/unix filesystems) in short: each filesystem keeps data (files) in its own way.
whan you're setting a new filesystem on partition, you have to erese all existing data on it. in short: if you didn't copy it into cd/dvd/another disc/another partition, you will lose it (ok, maybe *not necessary*, some files *may* be recovered- but it's not easy not fast and absolutelly not sure that it'll succeed).

btw, if you use this disc on windowsxp/2000/vista system, chose ntfs filesystem
if not, choose ext3 (maybe not the fastest, but the most safe imo)

---

### Post by intense.ego on 2008-02-03
So, basically, if i want to change the filesystem type, I have to move all my data to somewhere else or it will all be deleted?

---

### Post by szymon_g on 2008-02-03
yes.
this is the best way to save them- as far i know.

---

### Post by polmir on 2008-02-03
Read this info from this sites
[http://www.users.bigpond.net.au/hermanzone/p17.htm]("http://www.users.bigpond.net.au/hermanzone/p17.htm")
[http://www.users.bigpond.net.au/hermanzone/p17.htm#Why_integrity_check_your_downloaded_.iso]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Why_integrity_check_your_downloaded_.iso")
[http://www.users.bigpond.net.au/hermanzone/p17.htm#Checking_the_integrity_of_your_.iso_in_Windows]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Checking_the_integrity_of_your_.iso_in_Windows")

---

