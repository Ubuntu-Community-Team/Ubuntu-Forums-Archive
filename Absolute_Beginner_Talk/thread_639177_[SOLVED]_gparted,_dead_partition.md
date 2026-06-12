---
title: "[SOLVED] gparted, dead partition"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by markyb86 on 2007-12-12
I get this trying to mount sda1
root@ubuntu-dell:/home/bethyb# mount /dev/sda1
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
root@ubuntu-dell:/home/bethyb# 

This is after i erased a 2gb fat32 and combined it with sda8 in gparted.. Im confused

EDIT: I am an idiot. Dont mess around with ntfs drives in gparted unless you want to yield horrible results. I just deleted it and made it fat32 and ill use it that way for now on. Didnt lose too much, just my harddisk for virtualbox

---

