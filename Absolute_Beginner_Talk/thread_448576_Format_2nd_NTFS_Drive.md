---
title: "Format 2nd NTFS Drive"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Damnationie on 2007-05-19
I just recently installed Ubuntu 7.04 on an old Windows 2000 machine. This is my first Linux distro of any kind, being used as learning tool on my part.

The machine in question had two internal drives, a 40 gb and an 80 gb. The 40 gb was the primary drive for the OS and the 80 gb was the data drive, and I'm trying to replicate that set-up under Ubuntu. So, the install went fine. When I booted Ubuntu I found that it had reformated the 40gb drive as it's primary OS drive, as I wanted, but left the 80gb alone. I was surprised, but impressed, that Ubuntu could actually still see the NFTS filesystem on the 80gb drive, but since I did'nt want that stuff anymore, I sought to reformat the drive. This is where I ran into a problem.

After a certain amount of routing around I found out about chdisk, and used that to re-partition the 80gb drive. So, according to the fdisk -l, I now have the following drives

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4810    38636293+  83  Linux
/dev/sda2            4811        4998     1510110    5  Extended
/dev/sda5            4811        4998     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      158816    80043232+  83  Linux

With /dev/sdb being the 80 gb secondary drive. However, if I mount the drive and switch to it and do a directory list, it still shows all the old windows directory and files, which I had expected to be removed by the repartion. 

I've tried to manually delete the files both via the GUI and using rm to no avail. The files are listed as belonging to root so the GUI will not let me delete them. (As an aside is possibe to log in to the GUI as root?) Going in via the terminal as su any attempt to delete or even modify a file reports back an error "Read-only file system", which seems to imply that Ubuntu has protected the files. Anybody got any clue as to how I remove them off the disk ?

---

### Post by taurus on 2007-05-19
If you want to delete everything in /dev/sdb1 or reformat it to ext3, do

```
sudo umount /dev/sdb1
sudo mke2fs -j /dev/sdb1
```
Now, you need to add an entry in /etc/fstab so it would be mount automatically each time you boot.

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```
Save the change.  Create a new mount point if you haven't already done so and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by Damnationie on 2007-05-19
Thanks for that. Sorted out the deletion issue, but I had to do some more learning on chmod and chown in order to get a data directory set up so I could access. No worries though, I'm only starting to learn here. 

Thanks again.

---

### Post by taurus on 2007-05-19
_Assuming_ your login name is **john**, do

```
sudo chown -R **john**:**john** /media/sdb1
ls -la /media
```

Now, you are the proud owner of /media/sdb1 so you can write to it anytime you want.

---

