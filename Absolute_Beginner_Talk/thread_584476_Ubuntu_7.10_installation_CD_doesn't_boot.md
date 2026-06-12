---
title: "Ubuntu 7.10 installation CD doesn't boot"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by spylvas on 2007-10-21
Hi,

I have downloaded and burned several Ubuntu images, but all seems to behave same when I try to boot from CD. It only goes to text shell no mater what I chose from start up list. What I am doing wrong?

-S

---

### Post by GSF1200S on 2007-10-21
ooo.. im not really sure. You arent doing anything wrong I dont think.

What is your system, and its specs? This would help us figure this out.

Im assuming you want to use the LiveCD to try out Linux before you install it.

You can always use the alternate CD to install the system, but no gaurentees there either.

---

### Post by spylvas on 2007-10-21
My system
- Asus M2NPV-VM
- AMD 64 Dual Core 3800+
- 1GB Memory

I already have Ubuntu 7.04 running in my system without any problem, well maybe some, and that why I want to go to latest.

I tried alternate CD as well. Image I downloaded was fine, but disks I burned we corrupted.
I tried network install. GUI version will fail always same way:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)

text based install failed as well, but I am not sure if it was same error or something else.

---

### Post by spylvas on 2007-10-21
I removed quite from boot options and now I can see that there is some I/O errors on hda. 

after list of I/O errors in different logical blocks there is this line
hda: error code: 0x70 sense_key: 0x05 asc: 0xa8 ascq: 0x03

as I said same system is running ubuntu 7.04 just fine. And alternate CD seems to past this phase, but has some corruption problems later on.

---

### Post by spylvas on 2007-10-21
I solved this boot problem by changing cable I used for DVD/CDROM -drive. For some reason liveCD didn't like that cable. I got same error when I tried to boot with 7.04 liveCD. Funny thing here is that if I remember right I changed that vary same cable last time I installed 7.04 because I could boot with the cable I am using right now as I got I/O error... weird stuff!

---

