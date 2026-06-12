---
title: "install problems"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by charlier653 on 2006-07-14
My first install several days ago was on a 12.2 GB hdd, and in my ignorance have messed that one up.](*,) ](*,) :rolleyes: :???: 

I have tried several times to install on my primary SATA disk. It appears that the repartitioning of both disks was completed suscessfully, but the install hangs at 13%-15%. I have no idea what to do about this. Any suggestions?

Thanks,

Charlie

---

### Post by goodfren on 2006-07-14
Before installation, you can check cd for error during boot up, if there are error, then you have to reburn

---

### Post by slimdog360 on 2006-07-14
I assumed you used the same dick to install it the first time so if that worked it probably means that the cd is fine. But maybe it got sratched or something afterwards? maybe try checking the cd for errors first then come back and tell us what happened.

---

### Post by charlier653 on 2006-07-14
ok, i'll doublecheck the cd, which is the same one i burned for the initial install......

could it be a problem with the first install on the smaller disk?

(still thinking like winhell maybe?) my windoze experience has been that if there are any shreds of a previous install anywhere on the system a new install will fail..... but i don't think that is possible here, is it?

am currently in wifes XP machine.....

check finished, 0 checksums failed
press any key to reboot....

---

### Post by goodfren on 2006-07-14
I don't know about live cd but if you use installer cd, use install by oem instead of install be text, is much easier

---

### Post by charlier653 on 2006-07-14
grasping at straws here, could it ba a problem with my wanting to install on the SATA drive? didn't have any problems with installing on the IDE 0.

BTW, I have sysbios set for sata as IDE instead of raid.

will try using the HDA as / and SDA as /home and see if that makes a difference.

[edit]: just went through a mem test....have a bad 512 stick...removed, and am trying again:

sda1 as /
dha1 as /home

---

### Post by charlier653 on 2006-07-14
UPDATE:

Ubuntu finally installed, and auto mounted all partitions YAY!!;) I can now get to my NTFS partition with our website on it, will need to figure out how to reconfigure for linux, so may have to bother a few of you for further help.

---

