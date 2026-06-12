---
title: "permission denied?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by CurtZX on 2007-08-05
Trying to do what I believe is a copy and paste from an external drive to the internal drive..although it gives me a 'permission denied'... Any suggestions?


dd: opening `/dev/hda': Permission denied
curtis@curtis-laptop:/media/New Volume$

the command I am trying to run looks like this (with the exception of the file name I am copying)

dd bs-1048576 if=./filename.img of=/dev/hda

---

### Post by fatfranko on 2007-08-05
is the drive your trying to copy to ntfs?

---

### Post by wolfen69 on 2007-08-05
in terminal:
```
sudo apt-get install ntfs-config
```
then go to applications>system tools>ntfs config

---

### Post by aysiu on 2007-08-05
It could be any number of issues (I don't think you can *dd* a mounted drive, for example). Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by CurtZX on 2007-08-05
this is exactly what I get 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9545    76670181   83  Linux
/dev/hda2            9546        9729     1477980    5  Extended
/dev/hda5            9546        9729     1477948+  82  Linux swap / Solaris
curtis@curtis-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              72G  1.9G   67G   3% /
varrun                248M   84K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
udev                  248M   96K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   19M  230M   8% /lib/modules/2.6.15-26-386/volatile
curtis@curtis-laptop:~$ cat /etc/fstab

---

### Post by Nekiruhs on 2007-08-05
> **CurtZX said:**
> Trying to do what I believe is a copy and paste from an external drive to the internal drive..although it gives me a 'permission denied'... Any suggestions?


dd: opening `/dev/hda': Permission denied
curtis@curtis-laptop:/media/New Volume$

the command I am trying to run looks like this (with the exception of the file name I am copying)

dd bs-1048576 if=./filename.img of=/dev/hda
stupid question. Do you have root privelages? try 
```
sudo dd bs-1048576 if=./filename.img of=/dev/hda

```

---

### Post by proalan on 2007-08-05
probably another obvious point

also check the ownerships / permissions of the files being copied.

I previously had the same problem with pictures and music files.

---

### Post by aysiu on 2007-08-05
> **CurtZX said:**
> Trying to do what I believe is a copy and paste from an external drive to the internal drive..although it gives me a 'permission denied'... Any suggestions?


dd: opening `/dev/hda': Permission denied
curtis@curtis-laptop:/media/New Volume$

the command I am trying to run looks like this (with the exception of the file name I am copying)

dd bs-1048576 if=./filename.img of=/dev/hda What's **./filename.img** supposed to be? Doesn't **./** usually mean *execute the file*? Presumably, you'd want to do something like ```
dd bs-1048576 if=/media/New\ Volume/filename.img of=/dev/hda
```

> **CurtZX said:**
> this is exactly what I get 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9545    76670181   83  Linux
/dev/hda2            9546        9729     1477980    5  Extended
/dev/hda5            9546        9729     1477948+  82  Linux swap / Solaris
curtis@curtis-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              72G  1.9G   67G   3% /
varrun                248M   84K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
udev                  248M   96K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   19M  230M   8% /lib/modules/2.6.15-26-386/volatile Well, permission is being denied because you're currently using /dev/hda. /dev/hda1 is mounted as the / filesystem right now. I think you have to *dd* from one unmounted disk image to another unmounted disk.

Your best bet would be the boot the Ubuntu Deskop CD as a live CD and then mount the external drive and ```
sudo dd bs-1048576 if=/media/New\ Volume/filename.img of=/dev/hda
``` > curtis@curtis-laptop:~$ cat /etc/fstab Nothing came out for /etc/fstab?

---

### Post by Nekiruhs on 2007-08-05
> **aysiu said:**
> What's **./filename.img** supposed to be? Doesn't **./** usually mean *execute the file*? Presumably, you'd want to do something like ```
dd bs-1048576 if=/media/New\ Volume/filename.img of=/dev/hda
```

 Well, permission is being denied because you're currently using /dev/hda. /dev/hda1 is mounted as the / filesystem right now. I think you have to *dd* from one unmounted disk image to another unmounted disk.

Your best bet would be the boot the Ubuntu Deskop CD as a live CD and then mount the external drive and ```
sudo dd bs-1048576 if=/media/New\ Volume/filename.img of=/dev/hda
```  Nothing came out for /etc/fstab?
Actually Aysiu, I was informed that ./ was used to specify that the file was in the current directory. I could be wrong tho.

---

### Post by CurtZX on 2007-08-05
> **aysiu said:**
> What's **./filename.img** supposed to be? Doesn't **./** usually mean *execute the file*? Presumably, you'd want to do something like ```
dd bs-1048576 if=/media/New\ Volume/filename.img of=/dev/hda
```

 Well, permission is being denied because you're currently using /dev/hda. /dev/hda1 is mounted as the / filesystem right now. I think you have to *dd* from one unmounted disk image to another unmounted disk.

Your best bet would be the boot the Ubuntu Deskop CD as a live CD and then mount the external drive and ```
sudo dd bs-1048576 if=/media/New\ Volume/filename.img of=/dev/hda
```  Nothing came out for /etc/fstab?

I will get out of the OS and boot from the live and see what I can come up with here.. The .img file is to be executed if everything works properly.. it is another operating system that will be written to the hard drive from the external hard drive (pending I can make it work!) lol

---

### Post by apswartz on 2007-08-05
shouldn't the output be to a partition rather than the hard drive itself? Wouldn't the command, as written, replace (i.e., wipe out, erase, replace) all the contents on your hard drive?

---

### Post by ayenack on 2007-08-05
Try this in terminal.

sudo chown -R user:user /path/to/dir/

Where user = your user name in both instances and path is the path to the directory you want to copy to or from. As far as I know Fat FS does not support permissions so you have either NTFS or ext# I would think.

I think this will be sudo chown -R curtis:curtis /path/to/dir/ for you.

**DON'T USE chown ON ROOT FILES this can mess your system up.**

This should work.

You can also do this from nautilus of course like this.

gksudo nautilus

And then go to filesystem and select either the drive or the dir you want to change. Please be careful this is a powerful tool and can do untold damage.

BTW this to change permissions on the drive/dir not to copy the files, once you have changed permission on the drive you should be able to copy etc. A good tip if you are installing Ubuntu or any GNU Linux OS is to not to connect your external drives during install then when you plug them in as the user they will be owned by you and not root.

Would be a good idea to post the results cat /etc/fstab as aysiu suggested.

---

### Post by Mwelsh on 2008-01-15
I am having a similar problem and am wondering if anyone can help me. I'm trying to copy a hard drive image from my /dev/hda across a network. I PXE booted the client that has the image I want so that it's not running on the image and therefore should be accessible. However, for some reason, the kernel I have for the PXE does not have the sudo command, but I should have root power and access.

However, here's the problem:
```

dd bs=64k if=/dev/hda | nc ****.****.****.**** ****
/dev/hda: No such device or address

```

and on the Server:
```

nc -l -v -p **** | dd of=/tftpboot/imagetest.file bs=64K

```

A lot of commands don't work on the kernel I have, and there is no vim or nano editor. I'd appreciate any help!

Thanks a ton

---

