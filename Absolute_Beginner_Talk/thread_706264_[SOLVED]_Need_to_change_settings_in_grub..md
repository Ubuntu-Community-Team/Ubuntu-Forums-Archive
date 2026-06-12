---
title: "[SOLVED] Need to change settings in grub."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by percy_vere_uk on 2008-02-24
Hi

Just been tinkering (as one does and always regrets it) changing things around in unallocated disk space. I assume this has changed the partition numbers. Now when I try to boot up into gutsy I get the error message: 

Grub loading stage 1.5
grub loading, please wait
error 22

It hangs there so, I will need to get into grub and change these settings. I have the  live cd but do not know how to access the installed system from this.

percy

---

### Post by LaRoza on 2008-02-24
You can restore grub from the backup you made before you messed with it.

(Barring that, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351))

---

### Post by glennric on 2008-02-24
Boot to the live cd and open a terminal.  Then type "sudo fdisk -l"
This will give you a list of all of the partitions on all the harddrives on your system.  Then make a directory somewhere to mount a particular drive and type
```
sudo mount /dev/??? /pathto/mntpt
```
where ??? is the device name of the partition from fdisk and /pathto/mntpt is the full path of the place you want to mount the drive.
Also check out 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
and perhaps
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")
to restore or reinstall grub.

---

### Post by percy_vere_uk on 2008-02-24
Thanks for your prompt replies on this I am sure [http://ubuntuforums.org/showthread.p...t=grub+restore](http://ubuntuforums.org/showthread.p...t=grub+restore)
will sort the problem.

percy

---

