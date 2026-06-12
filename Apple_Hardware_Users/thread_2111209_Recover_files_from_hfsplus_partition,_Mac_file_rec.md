---
title: "Recover files from hfsplus partition, Mac file recovery"
date: 2013-02-01
forum: Apple Hardware Users
---

### Post by SBFree on 2013-02-01
Hi:
A coworker says they 'lost' their Mac laptop drive and had no backup of media files. He gave me the drive. I would like to recover the media he wants.
I connected the drive and gparted describes it as having 3 partitions:
a fat32 EFI, and two hfs+ partitions called Macintosh HD & Recovery HD.
I can mount the partition hfs+ partition 'Macintosh HD'
with 
mount -t hfsplus /dev/sdb2 /mac
but get a permission denied message trying to open or copy the folders that look like media.
I do not want to write to the drive by changing the file permissions.

Is there a way for me to copy folders from this drive without changing the permissions of the folders?

Thanks,
Scott

---

### Post by iMac71 on 2013-02-02
try to install [hfsplus tools]("https://launchpad.net/ubuntu/+source/hfsplus") by giving the following command in a Terminal window:```
sudo apt-get install -y hfsplus
```

---

### Post by SBFree on 2013-02-02
Thank you.
I can mount the partition and get to the folder "Users" and the specific user where the data probably is but folders within that will not open because of permission errors. I am also prohibited from copying those folders. I am hesitant to take ownership because it will write to the drive.

I tried to copy the partition to another drive with:
sudo dd if=/dev/sdb2 of=/dev/sda1 conv=notrunc,noerror

I loaded hfsplus tools and then tried to mount the copied partition. When I tried to mount it I got:
xubuntu@xubuntu:~$ sudo mount -t hfsplus /dev/sda1 /recov
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for any further insights.
Scott

---

### Post by iMac71 on 2013-02-03
If hfsplus doesn't solve the trouble, I fear that the only way to recover those data be to connect that drive to another Macintosh and to copy them on it.
Or, alternatively, if there aren't other Macintoshes, you might try to connect that drive to a PC running XP (I experienced that that OS doesn't care too much about file permissions), and then to copy them on it and finally to copy them from it on your PC (copying from XP to Ubuntu works fine).

---

### Post by SBFree on 2013-02-08
Personally I don't have a Mac to use the recovery software mentioned above. I did manage to get all the data off by two methods.
One was using photorec and the other
was to create a temporary user with UID 501 ( the id assigned to the files on the HD ). This let me have access to all the files on the drive. Thanks everyone for the help.
SB

---

