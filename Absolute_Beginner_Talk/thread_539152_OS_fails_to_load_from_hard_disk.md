---
title: "OS fails to load from hard disk"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by ahaugen on 2007-08-30
I recently installed Ubuntu from a CD image and now when I try to boot up from the Hard disk i get the "run_program:  '/sbin/modprobe'  abnormal exit" error.

I'm using a Sony Vaio with an AMD Athlon XP 1.5 ghz processor and 480 mb of ram

---

### Post by chuckyp on 2007-08-30
Bring up the grub menu and try to boot in recovery mode.

---

### Post by ahaugen on 2007-08-30
I keep getting the same error in recovery mode


EDIT:  i got something saying "/dev/disk/by-uuid/d6d6cb36-b5c-4a84-a049-192af79683e0" does not exist

---

### Post by Sef on 2007-08-30
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Did you check the cd for defects?

---

### Post by ahaugen on 2007-08-30
1.  no idea what md5sum is

2.  the burn speed was set to "best" so I'm assuming it ran somewhere between 5x and 7x

3.  yes, i checked the disc using the live CD boot and no errors were reported

---

### Post by Sef on 2007-08-30
[Md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") checks that the download is good.

---

### Post by jrusso2 on 2007-08-30
Do you have a flash drive installed?  If so remove it and try again

---

### Post by ahaugen on 2007-08-30
no, I don't have a flash drive on the computer

and can I run Md5sum off the iso burned to the DVD?

---

### Post by jrusso2 on 2007-08-31
have a look at this link

[http://ubuntuforums.org/showthread.php?p=2317401&highlight=feisty+uuid](http://ubuntuforums.org/showthread.php?p=2317401&highlight=feisty+uuid)


[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

if you don't have the jmicron controller you might need to try another distro or maybe gutsy beta

---

