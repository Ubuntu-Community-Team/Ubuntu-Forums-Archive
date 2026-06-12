---
title: "brand new amd 64 laptop will not boot live cd"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by havedampton on 2007-02-09
Hey,

I'm trying to add ubuntu as a second os.

I have a brand new hp dv6000 series laptop with an amd turion 64. I have made a partition using vista and tried the live cd with both the partition formatted as FAT32 and unallocated and neither is successful.

The ubuntu 64bit live cd will not boot, everything seems to go fine until I get a 
mount error which it pauses and passes and then hangs on something later, the furthest I've gotten in the network config.

I have a real bad-*** here with me and we're both stumped. 

help!

Thanks in advance.

---

### Post by renzokuken on 2007-02-09
have you tried passing the "noapic" option at boot?

---

### Post by jvc26 on 2007-02-09
Have you checked the md5 checksum of the download and have you error checked the disk as it may well be due to a bad download/bad burn.
Il

---

### Post by jd65pl on 2007-02-09
.

---

### Post by jd65pl on 2007-02-09
Is your optical drive the IDE kind? Is it controlled by a jmicron chip? If so try edgy 32bit. There is a problem with this chip in dapper

---

### Post by havedampton on 2007-02-09
no apic worked

Didn't download, have 6.06 cd from the mail.

Still can't get my built in wireless working.

---

### Post by renzokuken on 2007-02-10
have a look into ndiswrapper

---

